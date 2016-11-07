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
    <th>Specifics</th> 
    <td>time-diffs<br/>logger wildcards</td>
    <td>...</td>
    <td>...</td>    
  </tr>
  <tr>
    <th>API (subjective)</th> 
    <td>easy</td>
    <td>easy</td>
    <td>overcomplicated</td>    
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
      
