<p align="center">
  <a href="https://github.com/jasonsoft/" target="blank"><img src="https://avatars.githubusercontent.com/u/90173752?s=200&v=4" width="120" alt="JasonSoft Logo" /></a>
  <a href="https://github.com/expressjs/express" target="blank" style="padding-left:10px;"><img src="https://camo.githubusercontent.com/0566752248b4b31b2c4bdc583404e41066bd0b6726f310b73e1140deefcc31ac/68747470733a2f2f692e636c6f756475702e636f6d2f7a6659366c4c376546612d3330303078333030302e706e67" height="120" alt="Express Logo" /></a>
</p>

# express-controller

Controller extension by express router middleware 🦀

[![NPM version][npm-img]][npm-url]
[![NPM Downloads][downloads-image]][npm-url]
[![License][license-img]][license-url]

### Installation

```bash
npm i --save @jasonsoft/express-controller
```

### Quick Start

```javascript
/**
 * Example: https://github.com/jasonsoft-net/jasonsoft-express-server
 * FilePath: /jasonsoft-express-server/app.js
 * Added by Jason.Song (成长的小猪) on 2021/09/28
 * CSDN: https://blog.csdn.net/jasonsong2008
 * GitHub: https://github.com/jasonsoft-net
 * Organizations: https://github.com/jasonsoft
 */
import Express from 'express';
/**
 * Import the ControllerProvider from @jasonsoft/express-controller
 */
import { ControllerProvider } from '@jasonsoft/express-controller';

const app = new Express();
/**
 * Inject the controller directory
 */
ControllerProvider.initControllers({
  router: app,
  /** The default directory is './src/controllers' */
  dir: './app/controllers',
});

/** Service port */
const port = Number(process.env.PORT || 3000);

/** Listening port */
app.listen(port, () => {
  console.log(
    `[\x1B[36mRunning\x1B[0m] Application is running on: http://localhost:${port}`,
  );
});
```

```javascript
/**
 * Import Controller, Get, Post, Put, Delete, Patch, Options, Head, All, etc. decorators
 */
import {
  Controller,
  Get,
  // Post,
  // Put,
  // Delete,
  // Patch,
  // Options,
  // Head,
  // All,
} from '@jasonsoft/express-controller';

/** Inject the controller decorator */
@Controller()
export default class AppController {
  constructor() {
    this.message = {
      title: 'Welcome to use jasonsoft-express-server template',
      author: 'Jason.Song',
      github: 'https://github.com/jasonsoft-net',
      organization: 'https://github.com/jasonsoft',
    };
  }

  /**
   * GET http://localhost:3000/
   */
  @Get()
  async index() {
    return this.message;
  }
}
```

```javascript
/**
 * Import Controller, Get, Post, Put, Delete, Patch, Options, Head, All, etc. decorators
 */
import {
  Controller,
  Get,
  // Post,
  // Put,
  // Delete,
  // Patch,
  // Options,
  // Head,
  // All,
} from '@jasonsoft/express-controller';

@Controller('users')
export default class UsersController {
  constructor() {
    this.users = [
      {
        id: 1,
        username: 'jason',
      },
      {
        id: 2,
        username: 'steve',
      },
    ];
  }

  /**
   * GET http://localhost:3000/users
   */
  @Get()
  async getUsers() {
    return this.users;
  }

  /**
   * GET http://localhost:3000/users/1
   */
  @Get(':id')
  async getUserById(req) {
    const { id } = req.params;
    return this.users.find((user) => user.id === +id);
  }
}
```

![controller loading](https://github.com/jasonsoft/express-controller/raw/main/controller-loading.jpg)

### [完整示例 Example](https://github.com/jasonsoft-net/jasonsoft-express-server)

[npm-img]: https://img.shields.io/npm/v/@jasonsoft/express-controller.svg?style=flat-square
[npm-url]: https://npmjs.org/package/@jasonsoft/express-controller
[downloads-image]: https://img.shields.io/npm/dt/@jasonsoft/express-controller.svg?style=flat-square
[license-img]: https://img.shields.io/badge/license-MIT-green.svg?style=flat-square
[license-url]: LICENSE
