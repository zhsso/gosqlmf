#gosqlmf
Fetches results from SQL rows into a map - Go language

##Status
Completed YES

Tested YES

##Usage

### Fetching one row
```
  // Classic database connection and query 

  database, err := sql.Open(`postgres`, `user=foo dbname=bar password=secret`)
  defer database.close()
	
  rowPlayer, err := database.Query(`SELECT name,score FROM player WHERE id = 67`)
	if err != nil {
		panic(err.Error())
	}

  // Fetch into a map
  
	ok, mapPlayer, err := gosqlmf.FetchOne(rowPlayer)
	if err != nil {
		panic(err.Error())
	}
  
  // now can you do things like...
  if ok { // ok = fetched
    fmt.Printf("%d\n", mapPlayer["score"].(int64) )
  }
```
