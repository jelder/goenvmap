# env

A convenience wrapper around `os.Environ` and `os.GetEnv`. Use `ENV[]` like you do in other languages, plus safety, default values, and typesafe getters.

```go
package main

import (
	"fmt"
	. "github.com/jelder/env"
)

var ENV EnvMap

func main() {
	ENV = MustLoadEnv()
	fmt.Println("Hello,", ENV["USER"])
	fmt.Println("Presence helpers:", ENV.IsSet("DYNO"))
	fmt.Println("Defaults, like Ruby's Hash#fetch:", ENV.Get("MISSING", "yes!"))
	fmt.Printf("And type casting,\n%q\n%q\n",
		ENV.GetNumber("WORKERS", 8),
		ENV.GetBool("MY_OPTION"),
	)
}
```