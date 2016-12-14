
最後更新： 2016-03-29             

```
npm install --save mssql
```

```js
var sql = require('mssql');
var squel = require("squel").useFlavour('mssql');
var jsonfile = require('jsonfile');

/*
var config = {
  user: 'username',
  password: 'password',
  server: 'localhost', 
  database: 'database',
}
*/

var config = {
  user: 'john',
  password: 'doe',
  server: 'localhost', 
  database: 'my_database',
}

var q = squel.select().from('Employee').toString();

var connection = new sql.Connection(config, function(err) {
  // Query 
  var request = new sql.Request(connection);
  var file = 'data.json'; 
  // request.query('SELECT * FROM Employee', function(err, recordset) {
  request.query(q, function(err, recordset) {
    console.dir(recordset);
    jsonfile.writeFile(file, recordset, function (err) {
      console.error(err);
    });
  });
   
});

```

```
CREATE PROCEDURE [dbo].[sp_demo] 

@ID Int,
@Total Tinyint = 0 Output,
@Teststring Varchar(100) = 'Default' Output
AS

SET @Teststring = "Modifed"

SET @Total = 100

SELECT ID, Name, Lastname
FROM Table
WHERE ID = @id
```

```js
var sql = require('mssql');
var squel = require("squel").useFlavour('mssql');
var jsonfile = require('jsonfile');

var config = {
  user: 'john',
  password: 'doe',
  server: 'localhost', 
  database: 'my_database',
}

var connection = new sql.Connection(config, function(err) {
   
  // Stored Procedure 
    
  var request = new sql.Request(connection);
  request.input('ID', sql.Int, 10);
  request.output('Total', sql.Int, 10);
  request.output('Teststring', sql.VarChar(100));
  request.execute('sp_demo', function(err, recordsets, returnValue) {
    console.dir(recordsets);
    console.log(request.parameters.Total.value); // output value
    console.log(request.parameters.Teststring.value); // output value 
  });
});

```



---

### :books: 參考網站：
- [mssql](https://www.npmjs.com/package/mssql)
- [squel](https://www.npmjs.com/package/squel)
- [jsonfile](https://www.npmjs.com/package/jsonfile)

