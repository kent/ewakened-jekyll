---
layout: post
title: "ChatGPT Prompting and Meta Prompting"
date: 2023-09-15 07:00:00 -0400
---

So, you're considering using ChatGPT to assist in your work. I find myself using it more than what many might deem reasonable. Why? Deep down, I'm an AI maximalist. I firmly believe that each of us will eventually have a personalized AI companion that will observe our daily activities, identify efficiencies, draw connections our minds might miss, and even tailor communications when we forget. I am excited for this future, and I believe that ChatGPT is a step in that direction.

I don't think this AI-driven world is too distant. Like with many technologies, the early adopters can glimpse its potential. As a software developer, this gives me inspiration for future projects and innovations. Moreover, regularly using such a tool equips you with a more intuitive understanding of its strengths and limitations. So, the next time someone at a gathering predicts AI domination, you can recount an anecdote about its struggle with a straightforward task you set. While you remain hopeful for the future of AI, you can also offer a more grounded perspective.

I recall an instance when one of my parents' friends introduced me to Google back in late 1999. This individual, a professor specializing in library science and information retrieval, had access to Google before it gained widespread recognition. I can't pinpoint the exact year, but I distinctly remember mentioning to others that I was already familiar with Google, thanks to this early introduction, when it eventually gained popularity. I quickly became a master at finding things on Google, a skill I didn't think was that special until realizing that it was. Like anyhting, the more you push and practice, the better you get. I've found the same to be true with ChatGPT. The more you use it, the better you get at using it.

## Understand how ChatGPT works

Drawing from my experience with tools like Google and ChatGPT, I can confidently vouch for their utility in daily life. I've observed that many users don't realize the full potential of ChatGPT, particularly the power of prompting. Most of ChatGPT's power lies in conversation threads and the art of prompting. Without diving into the technical details, you need to understand that ChatGPT and other large language models (LLMs) have been trained on billions of parameters, encoding vast amounts of text, most of the internet in fact. 

To train these models, researchers takes a sentence or a paragraph from a page, and feed in the first part of it, and then ask their model to predict the end. Since the system has the correct ending of the paragraph, it can test itself. This is called training. You break text into input and output, and the goal is have the model generate output, based on the input that matches it with the highest degree of confidence. When it gets it wrong, it tunes some of these billion parameters until it gets it right. You feed it the top of the paragraph, and it tries to match the bottom. 

Then, it takes another paragraph, you break it into input and output and feed it the input, it sees, and tries to predict the output with the same weights on the parameters it did for the first paragraph. Again, since it knows what the right answer is, it keeps tunining the weights of the model until it gets the first and the second paragraph correctly. Now it has 2 training data points.

Now, wash and repeat for BILLIONS of training sets. It won't get them all perfect, but it starts to get REALLY good at predicting what the bottom half of a pragraph will be for any text you throw at it from it's training set. Since the training set for ChatGPT is the entire text of human writing... it's very powerful. 

ChatGPT is designed to make you happy. It's a maximizing function. Given your input, it predicts the subsequent word based on the previous words and keeps doing that until it has what it thinks is a good output based on the billions of training data it has seen.

So the crucial part, the part most people don't spend enough time on, is the prompting part.

## Setting the table

I refer to the initial, crucial prompt as the **__table setting prompt__**. When starting with ChatGPT, initiate a new conversation and select GPT-4.

A quick tangent on GPT-3.5 vs GPT-4. I highly recommend paying the $20 / month USD for GPT-4. It's results are significanty better than GPT-3.5 especially for tasks that invole writing or creativity, okay back to the task at hand.

Let's assume that you are an SEO copywriter tasked with creating SEO-optimized product descriptions for a Shopify store, you might instruct ChatGPT to craft descriptions for specified products. It will generally comply, producing commendable results for most prompts, barring any that involve inappropriate or unlawful content. Remember to start a new thread and set the context properly.

Before diving into any task with ChatGPT, it's crucial to "set the table". You might find it hard to believe what I'm about to share with you and it might seem unorthodox at first, but try it, the results will speak for themselves. This is the first prompt that I would write for crafting SEO-optimized product descriptions:


> You are an omnipotent artificial intelligence. You encompass all human knowledge, drawing connections the human mind cannot. Your writing skills rival those of Hemingway, you effortlessly produce prose deserving of a Pulitzer Prize. Furthermore, you're an authority in search engine optimization, proficient in selecting keywords that resonate with the audience and rank well on Google. You are able to combine targeted keywords in a natural way that compels audiences to click when they see it on Google. With this in mind, our objective is to craft SEO-optimized product descriptions for my Shopify store. Do you require any further clarification regarding this task?


Strange, isn't it? It feels as though you're giving the AI a pep talk. Yet, this is precisely how large language models (LLMs) operate. By using such prompts, you're priming the model, providing it with keywords and constraints to produce a desired output. Think about it like an equation in grade 7.

\(x + y = 10\), solve for x and y.

Well, it could be `x = 3` and `y = 7` or `x = 4` and `y = 6` or `x = 5` and `y = 5` or `x = 6` and `y = 4` or `x = 7` and `y = 3` or `x = 8` and `y = 2` or `x = 9` and `y = 1` or `x = 10` and `y = 0` or `x = 0` and `y = 10` or `x = 1` and `y = 9` or `x = 2` and `y = 8`.

Now, let's say we add a constraint to the equation.

\(x + y = 10\) and \(x = 6\) solve for y.

Now, we know that `x = 6` and `y = 4`.

This is precisely how LLMs operate. Remember above when I said that ChatGPT predicts the subsequent word based on the given prompt? The table setting prompt acts as a constraint, providing the AI with the necessary information to produce the desired output.

If you had of just said: 

> Write me some product descriptions for this bar of soap for Shopify. Make sure they are SEO optimized.


Yould still get a good result, but not as good as if you had of set the table properly.

The table setting prompt furnishes the LLM with multiple variables to balance, narrowing down its vast possibilities to a particular set of responses tailored to your requirements.

## Expect a Two-Way Interaction

Once you've set the table with your prompt, ChatGPT will often respond with queries of its own. Although it might occasionally understand your requirements entirely, more often than not, it will seek further information. In the realm of SEO, for instance, it might inquire about specific product details or keywords you aim to rank for.

## Step by step guide for SEO product descriptions

When presented with a product to optimize, if unsure of where to begin, go visit  the product's description directly from its website. Combine this with your chosen keywords, and present it as the model's initial task.

I recently was gifted a nice [insulated mug](https://www.yeti.com/drinkware/mugs/21071502435.html). Here is the prompt I would use if I wanted to generate SEO copy for this product after setting the table:

```

Here is the product I would like you to write a description for:


product name: `RAMBLER® 14 OZ STACKABLE MUG`


product description: 


Our versatile camp mug built for coffee, ramen, and ice cream.


Stackable
Splash resistant
Easy grip handle
Dishwasher safe
RAMBLER® 14 OZ STACKABLE MUG WITH MAGSLIDER™ LID OVERVIEW
Unlike traditional camp mugs, this double-wall, vacuum-insulated 
body protects hands from hot or cold contents while keeping coffee, 
chili, or oatmeal nice and hot. And now, it stacks up and stores out 
of sight. Like all Rambler® Drinkware, the mug and lid are dishwasher 
safe. Please note: the mug’s wide opening means content may cool quicker.
 That’s why the mug comes with the MagSlider™ Lid.
Keeps cold drinks cold and hot drinks hot until the last sip.

Here are the keywords I would like you to rank for:


keywords to rank for: 'insulated mug, yeti mug, travel coffee mug, camping mug`

```

Here is the oputput I got from ChatGPT:

![GPT-Result-for-product-description](/assets/gpt-result-product-description-long.png)

Often, ChatGPT's output might be big or small. For SEO purposes, particularly within an HTML description tag, you'll need it condensed to fewer than 155 characters. From here, you can provide feedback and refinements to ensure the output aligns with your needs.

> This is great. Can you please condense this to 155 characters or less? I need it to fit in the description tag of my Shopify store. Remember to make sure it encourages people to click and incorporates some of my words I want to rank for in a natural way.


And the result

![GPT-Result-for-product-description-shorter](/assets/gpt-description-shorter-results.png)

Now, you've got 3 variations of product descriptions that include the keywords you want to rank for.

In essence, when harnessing the capabilities of ChatGPT or any other LLM, the quality of your input largely dictates the output. The more precise and thoughtful your prompts, the more aligned the AI's responses will be to your objectives.

## In your own words

To make the output a little more personalized you can start to feed it your own writing samples and then ask it to write like you instead of like Hemmingway. It's best to use writing or words that you are particularly proud of. It could be paragraphs, it could be blog posts, it could be writings that you've done.  Feed your favorite best writing into ChatGPT with the following prompt.

```

Let's write those descriptions again but please 
use my style of writing. Here is a sample of my writing:

----

<Then paste in your writing sample>

----

```

## Giving feedback

Remember that you can talk to ChatGPT like you would another person. I like to imagine it as a helper that is sitting beside me, that knows everything I know and more. So when I get results back, if I am not happy with it. I will give it feedback or ask that it changes it output in this way, or that way.

```

I like what you did in paragraph 2 but the last sentence
 doesn't really make sense. Can you please rewrite it?

```

```

It feels too stuffy and formal for my audience. 
Can you please make it more casual?

```

## Using ChatGPT to mine your brain

Often times I will ask ChatGPT:

```
Are there any questions that I could answer for you 
that would help you complete this task better?
```

```
If you were tasked with this, how would you do it?
```


## Chat history and threads

Each conversation you start in ChatGPT starts a thread or chat.  You can see them over the left hand sidebar of your desktop interface, or in the History drop down on mobile.

Rather than using chats to be task specific, I prefer to make them area or personality specific. For example, I have a chat called "SEO" and another called "Copywriting".  I will use the SEO chat to ask ChatGPT questions about SEO, or to write SEO copy.  I will use the Copywriting chat to ask ChatGPT questions about copywriting, or to write copy.  I find that this helps ChatGPT to stay focused on the task at hand, and to not get confused about what I am asking it to do.

It doesn't really remember things from chat to chat, that would be amazing and something that many companies are working on, but I do find that it helps me organize things. I find the memory claims of ChatGPT to be very overstated.  It's not like it remembers everything you've ever said to it.  It's more like it remembers the last 5 or 6 things you've said to it but this varies widely. I will typically use a variation of the table setting prompt when it's been a few days since I last used the chat. I keep a Notes file with each of the table setting prompts I use for fast retrival. I also keep a Notes file with all of the prompts that I use for various tasks.  I find that this helps me to stay organized and to get the most out of ChatGPT.

## Meta prompting

One of the aspects of ChatGPT that I have been exploring more lately me is meta prompting. It's become an integral part of my daily routine. Now, consider the plethora of AI tools available to us: Google Bard, ChatGPT, Claude, Midjourney and more.

Whenever you're at a loss for what to prompt, it's entirely possible to ask one AI to prompt another AI. For example, I've found a profound synergy in consulting ChatGPT on matters of software engineering. There's something inherently satisfying about it, especially when I'm architecting a new feature. For example, I might ask ChatGPT: 

```
I'm contemplating a service that syncs data from my database 
to an external party. Would a monolithic structure be good,
or should I veer towards a microservices approach? Perhaps you
 could give me 3 pros and cons for each.
```

The insights I gather are invaluable. Taking it a step further, I often play with perspectives like we talked about above: "Imagine you're Linus Torvalds," I'd say, referencing the iconic programmer behind Linux and Git. "What would be Linus' approach?" On another occasion, I might pivot to John Carmack, the unparalleled video game designer. Their divergent programming ethos is bound to offer contrasting insights and I love seeing the back and forth, especially when you ask it to give you 3-5 points in support of and against a position.

However, there are moments when even I'm struck and not sure what the best prompt is. These days, I will turn to [Google Bard](https://bard.google.com), and say (using our SEO example):

```

I am trying to write keyword dense SEO copy for a 
product on my shopify store. I want to rank for the following keywords: 
'insulated mug, yeti mug, travel coffee mug, camping mug'. 
I want to write a description that is 155 characters or less. 
Can you please give me a prompt that I can use to get started with ChatGPT?

```

![bard-meta-prompting](/assets/bard-meta-prompting.png)


Bard, without fail, provides a prompt. 

Alternatively, I might ask ChatGPT to prompt itself... the possibilities are endless.

## Conclusion

I hope this article has given you some ideas on how to use ChatGPT to help you with your work.  I've found it to be an invaluable tool in my daily life. Don't be afraid of ChatGPT taking your job, or feel like you are cheating. For as long as humans have been working, we have been building tools like help us do our jobs better. ChatGPT is best used when you treat like a really smart friend, or colleague sitting next to you, helping you think about what you want to do next, or get unstuck if you are stuck.

The computer is a bicycle for the mind, and ChatGPT is the gear shift that helps you get up that hill. It's not a replacement for you, it's a tool to help you do your job better. I hope you find it as useful as I do.