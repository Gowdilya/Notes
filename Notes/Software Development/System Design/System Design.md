1. [How would you design a social media app?](https://igotanoffer.com/blogs/tech/system-design-interviews#sm)
2. [How would you design X game?](https://igotanoffer.com/blogs/tech/system-design-interviews#game)
3. [How would you design a parking lot?](https://igotanoffer.com/blogs/tech/system-design-interviews#parking)
4. [How would you design a URL-shortening service?](https://igotanoffer.com/blogs/tech/system-design-interviews#url)
5. [How would you design a web cache?](https://igotanoffer.com/blogs/tech/system-design-interviews#cache)
6. [How would you design autocomplete for a search engine?](https://igotanoffer.com/blogs/tech/system-design-interviews#search)
7. [How would you design an API?](https://igotanoffer.com/blogs/tech/system-design-interviews#api)
8. [How would you design a messaging app?](https://igotanoffer.com/blogs/tech/system-design-interviews#messaging)
9. [How would you design an online file-sharing system](https://igotanoffer.com/blogs/tech/system-design-interviews#file)
10. [How would you design an e-commerce store](https://igotanoffer.com/blogs/tech/system-design-interviews#ecommerce)
11. [How would you design a ride-hailing / delivery app](https://igotanoffer.com/blogs/tech/system-design-interviews#ride)


**Ask clarifying questions**

- Is the interviewer looking for a design of the core features, or a high-level overview of the whole service?
- What are the constraints of the system?
- What are your assumptions? (traffic distribution, number of active users and tweets, read vs write-heavy)

**Design high-level**

- Back-of-the-envelope calculations: average KBs per tweet, size of new tweet content per month, read requests and tweets per second, etc.
- High-level components: write, read, and search APIs; types of databases; SQL vs NoSQL; etc

**Drill down on your design**

- Potential bottlenecks: adding a load balancer with multiple web servers, scalability issues, fanout service slowing down tweets and @replies, etc.
- Components that you could dive into: how a user views the home timeline or posts a tweet, the intricacies of the database design, etc.

**Bring it all together**

- Consider: does the final design address the bottlenecks you’ve identified? Does it meet the goals you discussed at the beginning of the interview? Do you have any questions for the interviewer?

https://www.youtube.com/watch?v=KmAyPUv9gOY

## Build Twitter
Ask clarifying questions!