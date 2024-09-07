# 👻 Horror stories from 🅰️ngular server side rendering in productionn 🚀 💥
---
I, thank you for coming, i'm very honored to be here.



## Hello  
<!-- todo : add a picture of me -->
- Hi, I'm [Benjamin Legrand](https://www.benjaminlegrand.net) 
- I'm a software engineer and architect at [onepoint](https://www.onepoint.net)
- I'm french
---
I'm french (sorry), i'm a software engineer and architect. I do mainly front-end, and angular has been my main tool since AngularJS pre 1.0.

I'm working for onepoint, we are a french consulting company, but with an eulisthic approach. 

I worked on a lot of different projects through the years and some used server side rendering with Angular and some did'nt use it.

I wanted to share some of the horror stories I've seen.


## Table of Contents

- server side rendering
- window is undefined
- transfer state


## Before we start

@angular/universal
       ===
@angular/ssr

---
// image they're the same picture
I'm gonna talk about server side rendering or universal, because it was the name of the package before. But now it's called @angular/ssr. It's the same thing, just a different name.
Who here has used server side rendering with Angular ???



### What is angular server side rendering ? (~5 minutes)


- single page apps behavior without SSR
  - // interaction schema
  - advantages.
  - until recently, it was the angular default ( now the cli asks if you want server render )


- server side rendered :
  - // interaction schema
  - notes: the work
  - but also, they run in different context, obviously no window api on the server, no file api on the client


- advantages of SSR, what problems does it solves?
  - SEO
  - loading times / performance
- what other issues does it bring:
  - developer knowledge



### Window is undefined (~5 minutes)

- context
  - what is the issue ? principles


- problem
  - DOM implementations (domino/ jsdom)
  - Injection token to the rescue / conditional rendering


- solutions
  - setup  a window Service
  - condition your code
  - avoid fileReplacements
  - use injection token with 



### Help, my API is requested twice. (~5minutes)


- context
  - an app that fetches json data from api to render 


- what is the issue ?
  - put twice the load
  - can't cache


- solution
  - transfer state to the rescue
  - how do I implement ?



### Oups... a memory leak ( 5 minutes ) 


- context
  - huge project with 50+ developers
  - one production release per sprint
  - no dev / prod parity


- what happened / what is the issue
  - the Observer pattern
  - schema / link between objects


- how do garbage collection work
- we put the code on production
  - here is a normal schema of CPU / MEMORY usage
 

- solutions
  - remember kids, always unsubscribe.
  - do not initi



### The scandal of Inline Critical CSS ( 5 minutes )

- what is critical CSS
- what happened ?
  - huge team
- horror story of 300ms delays
- CPU usages through the roof



### The invisible infrastructure

- Context
- More recently i was asked to "check the SSR" on a project
- This was their architecture ( //todo schema )
- What is the issue ? = server side renderer always failed
- Solutions:
  - alerts and observability
  - do not run your code without logs
  - spa fallback is a good idea but:
  - a 500 error should NEVER happen



### The Localization Hell

- solution 1 : multiple apps, multiples build
- beware of the locale problem
- better solution : Accept-Language header 
- do not mix server lang source and browser lang sources 



### Lighthouse said our Content layout shift is bad


- context
  - let's say we have a banner, you don't want it 
  - 
- problem
  - now on loading
- what is content layout shift
- solutions
  - do not use local storage to store persistent page state.
  - use query params or cookies
  - take the cookies into consideration in the cache key



### Hydration ? not with this framework


- hydratation ?
- problem:
  - big loading time
  - page was emptied / re-rendered
  - huge cpu spike

- solutions
- preboot library
- angular 16 to the rescue



## Conclusion / Questions

- should you still do server-side-rendering?
- yes
- just know the traps and gotchas to avoid failures



## Thank you

- slides / openfeedback ?


