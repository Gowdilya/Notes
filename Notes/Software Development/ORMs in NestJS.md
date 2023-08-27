https://blog.logrocket.com/comparing-four-popular-nestjs-orms/#:~:text=ORMs%20in%20NestJS,need%20to%20write%20raw%20queries.

Object-relational mapping (ORM) is a technique that abstracts your database tables to data objects in memory. It allows you to query and write data to databases using data objects. ORMs are used to make database access easier, as developers won’t need to write raw queries.

[ORMs have their limitations](https://blog.logrocket.com/why-you-should-avoid-orms-with-examples-in-node-js-e0baab73fa5/), such as performance issues with complex queries, but they can still make your life easier when used in the right places.

NestJS is database-agnostic. For convenience, NestJS provides tight integrations with TypeORM and Sequelize out of the box with the @nestjs/typeorm and @nestjs/sequelize packages. You can also directly use any general purpose Node.js database integration library or ORM, but the ecosystem of NestJS ORMs is so massive, it can be daunting to choose the right one for your project.
