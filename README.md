# mono-redis

Redis module for [Mono](https://github.com/terrajs/mono).

[![npm version](https://img.shields.io/npm/v/@terrajs/mono-redis.svg)](https://www.npmjs.com/package/@terrajs/mono-redis)
[![Travis](https://img.shields.io/travis/terrajs/mono-redis/master.svg)](https://travis-ci.org/terrajs/mono-redis)
[![Coverage](https://img.shields.io/codecov/c/github/terrajs/mono-redis/master.svg)](https://codecov.io/gh/terrajs/mono-redis.js)
[![license](https://img.shields.io/github/license/terrajs/mono-redis.svg)](https://github.com/terrajs/mono-redis/blob/master/LICENSE)

## Installation

```bash
npm install --save @terrajs/mono-redis
```

Then, in your configuration file of your Mono application (example: `conf/application.js`):

```js
module.exports = {
  mono: {
    modules: ['@terrajs/mono-redis']
  }
}
```

## Configuration

Mono-Redis will use the `redis` property of your configuration (example: `conf/development.js`):

```js
module.exports = {
  redis: {
    port: 8047,
    // See https://github.com/NodeRedis/node_redis#options-object-properties for more argument
  }
}
```

## Usage

In your modules files, you can access `redis` instance like this:

```js
const { redis } = require('@terrajs/mono-redis')

redis.set('key', 'value', () => { console.log('value setted') })
redis.get('key', (value) => { console.log(`value is ${value}`)})

```

The current functions of redis client are using callback function but you can convert it to async function with the mono util

```js
const { redis } = require('@terrajs/mono-redis')
const utils = require('@terrajs/mono/utils')

await utils.cb(redis.set.bind(redis), 'key', 'value')
const result = await utils.cb(redis.get.bind(redi))
```

With [TypeScript](https://github.com/Microsoft/TypeScript):

```ts
import { redis } from '@terrajs/mono-redis'
```

