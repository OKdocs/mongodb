# mongodb
how to use mongodb (with go (what else???))

```go
	import "go.mongodb.org/mongo-driver/mongo"
```

```sh
go get 	"go.mongodb.org/mongo-driver/mongo"
```

## connecting


## structure

### document-objects
```go
type Developer struct {
		ID           primitive.ObjectID `json:"_id" bson:"_id"`
		CoffeesToday int                `json:"coffess" bson:"coffess"`
}
```
define go struct with `bson:` translation to mongodb fields

a struct whos fields have `bson` names can be given into crud functions and their returns can be unmarshalled upon

### primitives

```go 
import 	"go.mongodb.org/mongo-driver/bson/primitive"
```
```go
primitive.M{key:value}
primitive.M{string:interface{}}
```
is used to specify single mongodb document field, useful for filters and updates
```go
	"go.mongodb.org/mongo-driver/bson/primitive"
```
#### ID

```go
	ID := primitive.NewObjectID()
```

### collections

```go
	c := m.db.Collection("name")
```
assign pointer to collection "name" to variable c

## crud

All crud operations can be called with options that are defined in a operation specific options type.
```go
import	"go.mongodb.org/mongo-driver/mongo/options"
```
has to be imported to do so.
```go
opts := options.Update()
opts.SetUpsert(true)
```
example to get options for update and set the option to upsert

All crud operations come as FunctionOne and FunctionMany to either crud one or crund many entries

### create
```go
c.InsertOne(ctx, object, options...)
c.InsertMany(ctx, []object, options...)
```
objects can be structs whichs field names have `bson` defined or `map[string]interface{}`

### read
```go
c.FindOne(ctx, filter, options...)    
c.Find(ctx, filter, options...)                                 
```


#### aggregate
```go
c.Aggregate()                            // <- regular aggregate
```

### update
```go

```

### delete
