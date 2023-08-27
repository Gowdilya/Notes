https://docs.nestjs.com/techniques/mvc
https://www.youtube.com/watch?v=2h5NSwZ6neA
In order to create an MVC app, we also need a [template engine](https://expressjs.com/en/guide/using-template-engines.html) to render our HTML views:

```bash

$ npm install --save hbs
```

We've used the `hbs` ([Handlebars](https://github.com/pillarjs/hbs#readme)) engine, though you can use whatever fits your requirements. Once the installation process is complete, we need to configure the express instance using the following code:

main.ts

JS

```typescript

import { NestFactory } from '@nestjs/core';
import { NestExpressApplication } from '@nestjs/platform-express';
import { join } from 'path';
import { AppModule } from './app.module';

async function bootstrap() {
  const app = await NestFactory.create<NestExpressApplication>(
    AppModule,
  );

  app.useStaticAssets(join(__dirname, '..', 'public'));
  app.setBaseViewsDir(join(__dirname, '..', 'views'));
  app.setViewEngine('hbs');

  await app.listen(3000);
}
bootstrap();
```

We told [Express](https://github.com/expressjs/express) that the `public` directory will be used for storing static assets, `views` will contain templates, and the `hbs` template engine should be used to render HTML output.

#### Template rendering[#](https://docs.nestjs.com/techniques/mvc#template-rendering)

Now, let's create a `views` directory and `index.hbs` template inside it. In the template, we'll print a `message` passed from the controller:
```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <title>App</title>
  </head>
  <body>
    {{ message }}
  </body>
</html>
```


Next, open the `app.controller` file and replace the `root()` method with the following code:

app.controller.ts

JS

```typescript

import { Get, Controller, Render } from '@nestjs/common';

@Controller()
export class AppController {
  @Get()
  @Render('index')
  root() {
    return { message: 'Hello world!' };
  }
}
```

In this code, we are specifying the template to use in the `@Render()` decorator, and the return value of the route handler method is passed to the template for rendering. Notice that the return value is an object with a property `message`, matching the `message` placeholder we created in the template.

While the application is running, open your browser and navigate to `http://localhost:3000`. You should see the `Hello world!` message.



## Models
including ORM and data base access...

JS

```typescript

import { Get, Controller, Render } from '@nestjs/common';

@Controller()
export class AppController {
  @Get()
  @Render('index')
  root() {
    return { places: PlacesState };
  }
}
```