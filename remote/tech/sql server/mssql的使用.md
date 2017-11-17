const table = new sql.Table('table_name') // or temporary table, e.g. #temptable

table.create = true

table.columns.add('a', sql.Int, {nullable: true, primary: true})

table.columns.add('b', sql.VarChar(50), {nullable: false})

table.rows.add(777, 'test')

const request = new sql.Request()

request.bulk(table, (err, result) => {

    // ... error checks

})

Affected Rows

If you're performing INSERT, UPDATE or DELETE in a query, you can read number of affected rows. The rowsAffected variable is an array of numbers. Each number represents number of affected rows by a single statement.

Example using Promises

const request = new sql.Request()

request.query('update myAwesomeTable set awesomness = 100').then(result => {

    console.log(result.rowsAffected)

})

Example using callbacks

const request = new sql.Request()

request.query('update myAwesomeTable set awesomness = 100', (err, result) => {

    console.log(result.rowsAffected)

})

Example using streaming

const request = new sql.Request()

request.stream = true

request.query('update myAwesomeTable set awesomness = 100')

request.on('done', result => {

    console.log(result.rowsAffected)

})