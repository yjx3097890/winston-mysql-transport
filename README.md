A Mysql transport for [winston][0].

## Installation

### Installing winston-mysql-transport via npm

``` sh
  $ npm install winston
  $ npm install winston-mysql-transport
```
(or add it to your package.json)

## Usage

First you must generate your log table

``` sql
/*file : extras/schema.sql*/
CREATE TABLE IF NOT EXISTS `my_databse`.`log_table` (
	`id` int(10) NOT NULL AUTO_INCREMENT,
	`level` varchar(45) NOT NULL,
	`message` text NOT NULL,
	`timestamp` datetime NOT NULL,
	`meta` varchar(255),
	`hostname` varchar(255),
	PRIMARY KEY (`id`)
);
```

And in your code...

``` js
  var winston = require('winston');
  
  //
  // Requiring `winston-mysql-transport` will expose
  // `winston.transports.Mysql`
  //
  require('winston-mysql-transport').Mysql;
  
  options = {
  	database : "my_database",
  	table : "log_table",
  	user : "root"
  }
  
  winston.add(winston.transports.Mysql, options);
```

## Unsupported
This transport does not support (yet) :

* **streaming**

* **querying**

* **Saving of metadata**

[0]: https://github.com/flatiron/winston
