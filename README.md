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
    <td>5, custom</td>
    <td>5, custom</td>
  </tr>
  <tr>
    <th>Level filter</th>
    <td>-</td>
    <td>+</td>
    <td>+</td>
  </tr>
  <tr>
    <th>Multi-Loggers</th>
    <td>+</td>
    <td>+</td>
    <td>+</td>
  </tr>
  <tr>
    <th>Logger filter</th>
    <td>+</td>
    <td>+</td>
    <td>+</td>
  </tr>
  <tr>
    <th>Formats</th>
    <td>-</td>
    <td>good, custom</td>
  </tr>
  <tr>
    <th>Transports</th> 
    <td>console only</td>
    <td>console, file, SMTP, custom</td>
  </tr>
  <tr>
    <th>Specifics</th> 
    <td>time-diffs<br/>category wildcards</td>
    <td>...</td>
  </tr>
</table>

### Support

https://npmcompare.com/compare/bunyan,log4js,winston
