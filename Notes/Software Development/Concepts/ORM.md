**Object Relation Mapping.** Typically this means communicating with a system using a language other than the native language is expects.

An example of this would be a SQL database. A SQL database is expecting, well, a SQL query to interact with it, but what if we wanted to interact with it with something like a Golang program?

## What does an ORM do?

An ORM library gives us the mechanism by which to perform **Object Relation Mapping.** This means we end up with structs or classes that _represent_ something like a table in our database

In golang, we would get something like this:  

```
user := models.Users().ByID(1)
```

Which would generate the following SQL query:

```
SELECT * FROM Users WHERE id = 1;
```


Best TypeScript ORM
1. [Prisma](https://blog.logrocket.com/best-typescript-orms/#best-typescript-orms-prisma)
2. [TypeORM](https://blog.logrocket.com/best-typescript-orms/#best-typescript-orms-typeorm)


## [[Type ORM]]
https://typeorm.io/
```typescript
import { Entity, PrimaryGeneratedColumn, Column } from "typeorm"

@Entity()
export class User {
    @PrimaryGeneratedColumn()
    id: number

    @Column()
    firstName: string

    @Column()
    lastName: string

    @Column()
    age: number
}
```

And your domain logic looks like this:

```typescript
const userRepository = MyDataSource.getRepository(User)

const user = new User()
user.firstName = "Timber"
user.lastName = "Saw"
user.age = 25
await userRepository.save(user)

const allUsers = await userRepository.find()
const firstUser = await userRepository.findOneBy({
    id: 1,
}) // find by id
const timber = await userRepository.findOneBy({
    firstName: "Timber",
    lastName: "Saw",
}) // find by firstName and lastName

await userRepository.remove(timber)
```

Alternatively, if you prefer to use the `ActiveRecord` implementation, you can use it as well:

```typescript
import { Entity, PrimaryGeneratedColumn, Column, BaseEntity } from "typeorm"

@Entity()
export class User extends BaseEntity {
    @PrimaryGeneratedColumn()
    id: number

    @Column()
    firstName: string

    @Column()
    lastName: string

    @Column()
    age: number
}
```

And your domain logic will look this way:

```typescript
const user = new User()
user.firstName = "Timber"
user.lastName = "Saw"
user.age = 25
await user.save()

const allUsers = await User.find()
const firstUser = await User.findOneBy({
    id: 1,
})
const timber = await User.findOneBy({
    firstName: "Timber",
    lastName: "Saw"
})

await timber.remove()
```