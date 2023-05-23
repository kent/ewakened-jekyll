# Early Thoughts on Next.js Coming from Ruby on Rails

I have been a Ruby on Rails developer since the pre 1.0 days and truly do love the framework and all it has to offer. However, for those paying attention, around the time of Rails 4-5ish area the growing power of React and Node was becoming overwhealming and while DHH and Basecamp were still driving a ton of innovation on the front-end with their Basecamp.com re-write and the addition of webpacker, it became clear that the Rails way was falling short when compared to tools like React.

I recenty inherited a new front-end codebase written in React that didn't follow a ton of conventions and I was left evaluating front-end frameworks for a re-write. I looked at [React 18](https://react.dev/blog/2022/03/29/react-v18), [Remix](<https://remix.run/ >) and [NextJS.](https://nextjs.org/)

To be fair, I did look at [Hotwire](https://hotwired.dev/) and [Stimulus](https://github.com/hotwired/stimulus-rails) and even the [ReasonML framework](https://reasonml.github.io/) thanks to recommendation from React Core member: [Cheng Lou](https://twitter.com/_chenglou?lang=en) but I will save that for another post.&#x20;

I am currently settled on giving NextJS a try, fully commit and if it sucks... well it's just the front-end, easy to fix :)&#x20;

Disclaimer: I am less than 2 weeks into a NextJS rewrite, it's early days, but I have some impressions and takes worthy of a post already.

## Config vs. convention

If you are coming from Django or Rails, you will like that in NextJS everything has a place. It's definitiely convention over configuration which is nice, however, it's not as dogmatic as Rails or Django which I believe is a bug, not a feature. For all the shit that DHH takes, [the Rails Doctrine](https://rubyonrails.org/doctrine) is why so many folks love Rails, and why billions of dollars of value has been built on it's back.

Where do you put components?&#x20;

What's the best way to handle data-fetching?&#x20;

Are there naming conventions for the different kinds of components?&#x20;

All of these could use some good conventions!

## React, React, React

You have love React to love NextJS or at least learn to love React. I have had a troubled past with React. We were lucky at Tilt, we were one of the first companies outside of Facebook and Instagram that really embraced React in it's early days. We got to see and use it with some help from Facebook engineers before the public did and it was really cool at the time. A lot of the stuff that we were doing manually, it just soved for us. That being said, it's different. It's akin to learning how to write Haskell if you have only known Ruby or Python. It's a mind fuck and you have to embrace the pain and learn new patterns.

But NextJS is just react with some sugar on top. So you can always drop down into pure React components and get the job done.

## Server-Side Rendering

I haven't explored the different rendering schemes a lot yet in Next but it's deifnitelty a big reason I chose it over Remix for example. The good news is that it looks like the directives to convert something from server-side to client side is a simple deocrator at the top of the file and then NextJS will handle the caching and complexity for you. Sounds Rails-y, sounds great but I expect the devil will be in the details here.

## Routing

Alright, time for my hot take. Directory based rendering is not going to last for a long time in NextJS. It feels like a hacked way to go from their tradtional `/pages` magic to a more `/app` or `/src` based React app. Building folder structures and then giving your folders weird names with `[username]` syntax and then calling that in a view file feels weird.

This feels like a transitionary step and my guess is it won't last. It's fine, and works well, but coming from the Ruby / Rails / Sinatra world it feels like a toy that is made of plastic and not metal. It's brittle and will likely break.&#x20;

My hope is that they continue to get inspired by Rails, Django, Express etc and adopt a simple. \`routes\` file along with some generators or other conventions as to where your files should go, and then give you the power to break those conventions.

## Conclusion

Overall, Next.js is a powerful framework that's well worth considering if you're coming from a Rails background. I can't say NextJS is going to take the crown as my favourite framework from Rails anytime soon but I am enjoying it and it's well worth considering if you are coming from a Rails or Django background.&#x20;
