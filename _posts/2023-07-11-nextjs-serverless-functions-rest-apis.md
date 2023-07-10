---
layout: post
title: "Moving to Next.js Serverless Functions for REST APIs"
date: 2023-07-11 20:49:35 -0400
---

I've recently embarked on rewriting Agora using [NextJS 13](https://nextjs.org/docs/app/building-your-application/routing) and it's stirring up some serious déjà vu of my Rails and Django days back in 2007-2009. The premise of a framework-driven infrastructure resonates with me. Coupled with the prospect of partnering with Vercel, I'm eagerly anticipating a leaner, more efficient developer experience and a highly performant web app.

One of the most exicting new features is serverless function support. This feature, specific to NextJS 13+, has the potential to dominate as its adoption becomes more widespread. The concept is elegantly simple:

Create an `api` directory within your `app` directory. Inside `api`, create another directory named `v1`, and within `v1`, create a `users` directory. Inside the `users` directory, create a file named `routes.js`. Your directory structure should look something like this:

```plaintext
app
├── api
│   └── v1
│       └── users
│           └── routes.js
```

I understand if this feels a tad convoluted, especially for those of us accustomed to Sinatra, Flask, and other router-based frameworks. Designating routes as folders might seem inefficient, but bear with me. It's plausible that this folder structure may either fade away as a vestige of the old /pages architecture or prove beneficial from a hosting/infra standpoint. Time will tell.

Let's say we want a function that displays all our users. We'd write something like this in `route.js`:

```js
// src/app/api/v1/users/routes.js
import { NextResponse } from "next/server";
import { PrismaClient } from "@prisma/client";

export async function GET(request) {
  
  const prisma = new PrismaClient();

  let page = parseInt(request.nextUrl.searchParams.get("page"), 10);
  if (isNaN(page) || page < 1) {
    page = 1;
  }

  const pageSize = 25;
  const total_count = await prisma.users.count();
  const total_pages = Math.ceil(total_count / pageSize);

  const proposals = await prisma.users.findMany({
    take: pageSize,
    skip: (page - 1) * pageSize,
  });

  await prisma.$disconnect();

  // Build out proposal response
  const response = {
    meta: {
      current_page: page,
      total_pages: total_pages,
      page_size: pageSize,
      total_count: total_count,
    },
    users: users.map((proposal) => ({
      // Just testing out, not meant for production
      id: user.id,
      username: user.username,
    })),
  };

  return NextResponse.json(response);
}
```

But what if we need to authenticate API users against this function? No problem.

Create a `middleware` directory within your `src/app/lib` and add something like this:

```js
// src/app/lib/middlewear/authenticateAPIUser.js
import { NextResponse } from "next/server";
import { headers } from "next/headers";

export function authenticateAPIUser(request) {
  const headersList = headers();
  const apiKey = headersList.get("api-key");

  // Use your method of checking the API user's key
  const apiUser = validateAPIKey(apiKey);

  if (!apiUser || !apiUser.active) {
    return NextResponse.redirect(new URL("/api/forbidden", request.url));
  }

  return null;
}
```

Then go back and modify your `route.js` file to look like this:

```js
// src/app/api/v1/users/routes.js
import { NextResponse } from "next/server";
import { PrismaClient } from "@prisma/client";
import { authenticateAPIUser } from "src/app/lib/middlewear/authenticateAPIUser"

export async function GET(request) {

  // Check if the session is authenticated first
  const authResponse = authenticateAPIUser(request);
  if (authResponse) {
    return authResponse;
  }
  
  const prisma = new PrismaClient();

  let page = parseInt(request.nextUrl.searchParams.get("page"), 10);
  if (isNaN(page) || page < 1) {
    page = 1;
  }

  const pageSize = 25;
  const total_count = await prisma.users.count();
  const total_pages = Math.ceil(total_count / pageSize);

  const proposals = await prisma.users.findMany({
    take: pageSize,
    skip: (page - 1) * pageSize,
  });

  await prisma.$disconnect();

  // Build out proposal response
  const response = {
    meta: {
      current_page: page,
      total_pages: total_pages,
      page_size: pageSize,
      total_count: total_count,
    },
    users: users.map((proposal) => ({
      // Just testing out, not meant for production
      id: user.id,
      username: user.username,
    })),
  };

  return NextResponse.json(response);
}
```

Make sure that your `/app/api/forgidden` route is set up to return a 403 status code and you are good to go, you can use something like this

```js
// Forbidden route if API Autentication fails
import { NextResponse } from "next/server";

export async function GET(request) {
  return NextResponse.json({ error: "Forbidden" }, { status: 403 });
}
```

And put that in `/src/app/api/forbidden/routes.js`

There you have it. The ability to seamlessly scale out serverless functions—especially if you're using the same hosting environment for both front-end and back-end (e.g., Vercel)—is a game-changer.

Stay tuned for more discoveries as I continue to explore this exciting frontier.