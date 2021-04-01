# go-sessions-stores

[![Go Report](https://goreportcard.com/badge/github.com/bh90210/go-sessions-stores)](https://goreportcard.com/report/github.com/bh90210/go-sessions-stores)

Dgraph &amp; MongoDB implementations for [kataras/go-sessions](https://github.com/kataras/go-sessions).

## How to use

For a full documentation of the library see the [original repository](https://github.com/kataras/go-sessions).

Full examples can be found in the [examples](https://github.com/bh90210/go-sessions-stores/tree/main/examples) folder.

### Mongo

[![Mongo Reference](https://pkg.go.dev/badge/github.com/bh90210/go-sessions-stores/mongostore.svg)](https://pkg.go.dev/github.com/bh90210/go-sessions-stores/mongostore) 

To include `mongostore` run 
```sh
go get github.com/bh90210/go-sessions-stores/mongostore
```

#### Example

```go
	// replace with your running mongo server settings:
	cred := options.Credential{
		AuthSource: "admin",
		Username:   "user",
		Password:   "password",
	}

	clientOpts := options.Client().ApplyURI("mongodb://127.0.0.1:27017").SetAuth(cred)
	db, _ := mongostore.New(clientOpts, "sessions")

	sess := sessions.New(sessions.Config{Cookie: "sessionscookieid"})

	sess.UseDatabase(db)
```

### Dgraph

[![Dgraph Reference](https://pkg.go.dev/badge/github.com/bh90210/go-sessions-stores/dgraphstore.svg)](https://pkg.go.dev/github.com/bh90210/go-sessions-stores/dgraphstore) 

To include `dgraphstore` run 
```sh
go get github.com/bh90210/go-sessions-stores/dgraphstore
```

#### Example 

```go
	// replace with your server settings:
	conn, _ := grpc.Dial("127.0.0.1:9080", grpc.WithInsecure())
	db, _ := dgraphstore.NewFromDB(conn)

	sess := sessions.New(sessions.Config{Cookie: "sessionscookieid"})

	sess.UseDatabase(db)
```
