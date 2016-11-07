# Logging solutions compared

*The abscence of feature is not automatically BAD just and the presence is not automatically GOOD.*

### Features

<table>
  <tr>
    <th></th>
    <th><a href="https://github.com/visionmedia/debug">Debug<a/></th>
    <th><a href="https://github.com/nomiddlename/log4js-node">Log4Js</a></th>
    <th><a href="https://github.com/winstonjs/winston">Winston</a></th>
  </tr>
  <tr>
    <th>Levels</th>
    <td>1</td>
    <td>5</td>
    <td>6</td>
  </tr>
  <tr>
    <th>Custom Levels</th>
    <td>-</td>
    <td>+</td>
    <td>+</td>
  </tr>
  <tr>
    <th>Level Filter</th>
    <td>-</td>
    <td>+</td>
    <td>+</td>
  </tr>
  <tr>
    <th>Custom Loggers</th>
    <td>+</td>
    <td>+</td>
    <td>+</td>
  </tr>
  <tr>
    <th>Logger Filter</th>
    <td>+</td>
    <td>+</td>
    <td>+</td>
  </tr>
  <tr>
    <th>Formats</th>
    <td>-</td>
    <td>+</td>
    <td>+</td>
  </tr>
  <tr>
    <th>Custom Formats</th>
    <td>-</td>
    <td>+</td>
    <td>+</td>
  </tr>
  <tr>
    <th>Transports</th> 
    <td>console</td>
    <td>console, file, SMTP</td>
    <td>console, file, SMTP</td>
  </tr>
  <tr>
    <th>Custom Transports</th> 
    <td>-</td>
    <td>+</td>
    <td>+</td>
  </tr>
  <tr>
    <th>File Rotation</th> 
    <td>-</td>
    <td>+</td>
    <td>+</td>
  </tr>
  <tr>
    <th>JSON support</th> 
    <td>no</td>
    <td>no</td>
    <td>yes</td>    
  </tr>
  <tr>
    <th>Specifics</th> 
    <td>profiling<br/>logger wildcards</td>
    <td>...</td>
    <td>profiling<br/>querying(!)</td>    
  </tr>
</table>

### Support

https://npmcompare.com/compare/debug,log4js,winston

### Notes

* [Morgan](https://github.com/expressjs/morgan) – purpose? Trivial to implement on top of selected logger.

* JSON logging – [arguable](https://news.ycombinator.com/item?id=3896833). 

Initially I felt like Log4JS has better defaults so decided to stick with it.
Then I've found a significant drawback: Log4JS wants you to attach **transports** (called **appenders** there) to categories
rather than loggers themselves. So you cannot define levels per transports per loggers.

I may be wrong, but I belive this (basic) case is not possible to configure with Log4JS:

```
WINSTON
  mainLogger
    transports
      console
        DEBUG
      file  
        INFO
      SMTP
        ERROR
```      
      
Winston also understands exceptions so 

```js
try {
  throw Error("bad")
} catch (err) {
  logger.error(err)
}
```

logs valid JSON (note `\n`) (plain text is also configurable).

```json
{"message":"bad","stack":"Error: bad\n    at Object.<anonymous> (/.../test/winston.js:14:8)\n    at Module._compile (module.js:573:32)\n    at Object.Module._extensions..js (module.js:582:10)\n    at Module.load (module.js:490:32)\n    at tryModuleLoad (module.js:449:12)\n    at Function.Module._load (module.js:441:3)\n    at Module.runMain (module.js:607:10)\n    at run (bootstrap_node.js:382:7)\n    at startup (bootstrap_node.js:137:9)\n    at bootstrap_node.js:497:3","level":"error","timestamp":"2016-11-07T09:28:41.799Z"}
```

Usage experience: Winston is hands down better than Log4JS in almost all aspects. 
