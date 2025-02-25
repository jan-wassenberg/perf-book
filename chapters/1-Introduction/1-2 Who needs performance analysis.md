---
typora-root-url: ..\..\img
---

## Who Needs Performance Tuning?

Performance engineering does not need to be justified much in industries like High-Performance Computing (HPC), Cloud Services, High-Frequency Trading (HFT), Game Development, and other performance-critical areas. For instance, Google reported that a 2% slower search caused [2% fewer searches](https://assets.en.oreilly.com/1/event/29/Keynote Presentation 2.pdf)[^3] per user. For Yahoo! 400 milliseconds faster page load caused [5-9% more traffic](https://www.slideshare.net/stoyan/dont-make-me-wait-or-building-highperformance-web-applications)[^4]. In the game of big numbers, small improvements can make a significant impact. Such examples prove that the slower the service works, the fewer people will use it. 

There is a famous quote: "Premature optimization is the root of all evil". But the opposite is often true as well. Postponed performance engineering work may be too late and cause as much evil as premature optimization. For developers, working with performance-critical projects, it is crucial to know how underlying HW works. In such industries, it is a fail-from-the-start when a program is being developed without HW focus. Performance characteristics of a software must be a first-class-citizen along with correctness and security starting from day 1. ClickHouse DB is an example of a successful software product that was built around a small but very efficient kernel.

Interestingly, performance engineering is not only needed in the aforementioned areas. Nowadays, it is also required in the field of general-purpose applications and services. Many tools that we use every day simply would not exist if they failed to meet their performance requirements. For example, Visual C++ [IntelliSense](https://docs.microsoft.com/en-us/visualstudio/ide/visual-cpp-intellisense)[^2] features that are integrated into Microsoft Visual Studio IDE have very tight performance constraints. For IntelliSense autocomplete feature to work, they have to parse the entire source codebase in the order of milliseconds[^5]. Nobody will use source code editors if it takes them several seconds to suggest autocomplete options. Such a feature has to be very responsive and provide valid continuations as the user types new code. The success of similar applications can only be achieved by designing SW with performance in mind and thoughtful performance engineering.

Sometimes fast tools find use in the areas they were not initially designed for. For example, nowadays, game engines like [Unreal](https://www.unrealengine.com)[^6] and [Unity](https://unity.com/)[^7] are used in architecture, 3d visualization, film making, and other areas. Because game engines are so performant, they are a natural choice for applications that require 2d and 3d rendering, physics engine, collision detection, sound, animation, etc.

> “Fast tools don’t just allow users to accomplish tasks faster; they allow users to accomplish entirely new types of tasks, in entirely new ways.” - Nelson Elhage wrote in [article](https://blog.nelhage.com/post/reflections-on-performance/)[^1]on his blog (2020).

I hope it goes without saying that people hate using slow software. Performance characteristics of an application can be a single factor for your customer to switch to a competitor's product. By putting emphasis on performance, you can give your product a competitive advantage.

Performance engineering is important and rewarding work, but it may be very time-consuming. In fact, performance optimization is a never-ending game. There will always be something to optimize. Inevitably, the developer will reach the point of diminishing returns at which further improvement will come at a very high engineering cost and likely will not be worth the efforts. From that perspective, knowing when to stop optimizing is a critical aspect of performance work[^8]. Some organizations achieve it by integrating this information into the code review process: source code lines are annotated with the corresponding “cost” metric. Using that data, developers can decide whether improving the performance of a particular piece of code is worth it.

Before starting performance tuning, make sure you have a strong reason to do so. Optimization just for optimization’s sake is useless if it doesn’t add value to your product. Mindful performance engineering starts with clearly defined performance goals, stating what you are trying to achieve and why you are doing it. Also, you should pick the metrics you will use to measure if you reach the goal. You can read more on the topic of setting performance goals in [@SystemsPerformance] and [@Akinshin2019].

Nevertheless, it is always great to practice and master the skill of performance analysis and tuning. If you picked up the book for that reason, you are more than welcome to keep on reading.

[^1]: Reflections on software performance by N. Elhage - [https://blog.nelhage.com/post/reflections-on-performance/](https://blog.nelhage.com/post/reflections-on-performance/)
[^2]: Visual C++ IntelliSense - [https://docs.microsoft.com/en-us/visualstudio/ide/visual-cpp-intellisense](https://docs.microsoft.com/en-us/visualstudio/ide/visual-cpp-intellisense)
[^3]: Slides by Marissa Mayer - [https://assets.en.oreilly.com/1/event/29/Keynote Presentation 2.pdf](https://assets.en.oreilly.com/1/event/29/Keynote Presentation 2.pdf)
[^4]: Slides by Stoyan Stefanov - [https://www.slideshare.net/stoyan/dont-make-me-wait-or-building-highperformance-web-applications](https://www.slideshare.net/stoyan/dont-make-me-wait-or-building-highperformance-web-applications)
[^5]: In fact, it's not possible to parse the entire codebase in the order of milliseconds. Instead, IntelliSense only reconstructs the portions of AST that has been changed. Watch more details on how the Microsoft team achieves this in the video: [https://channel9.msdn.com/Blogs/Seth-Juarez/Anders-Hejlsberg-on-Modern-Compiler-Construction](https://channel9.msdn.com/Blogs/Seth-Juarez/Anders-Hejlsberg-on-Modern-Compiler-Construction).
[^6]: Unreal Engine - [https://www.unrealengine.com](https://www.unrealengine.com).
[^7]: Unity Engine - [https://unity.com/](https://unity.com/)

[^8]: Roofline model ([@sec:roofline]) and Top-Down Microarchitecture Analysis ([@sec:TMA]) may help to assess performance against HW theoretical maximums.