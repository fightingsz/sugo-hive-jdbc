# nodejs jdbc for hive

## install

```shell
npm i sugo-hive-jdbc
```


## example
```js
const HiveJdbc = require('sugo-hive-jdbc')

const conf = {
  url: 'jdbc:hive2://192.168.0.223:10000/default',
  drivername: 'org.apache.hive.jdbc.HiveDriver',
  minpoolsize: 10,
  maxpoolsize: 100,
  properties: {
    user: 'hive',
    password: ''
  }
}

const main = async () => {
  const hive = new HiveJdbc(conf)
  // const conn = await hive.getConnection()
  // query with params
  // const res = await hiveKit.runQuery('select * from users where userid=? limit 10', ['c81e728d9d4c2f636f067f89cc14862c'])
  // query without params
  const res = await hive.runQuery('select count(*) from users')
  console.log(res)
}

main()
```