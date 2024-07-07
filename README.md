### What is middleware pattern in web development?
- a design approach used to handle the flow of requests and responses in a web application
- Middleware functions are a series of processing steps through which the request passes before reaching the final handler (such as a route or controller) and the response is generated.
- Middleware can be used to execute code, modify the request or response objects, end the request-response cycle, and call the next middleware function in the stack.

### General middleware pattern in Go
```go
import "net/http"

func MyMiddleware(h http.Handler) http.Handler {}
```

### Implementing middleware pattern
```go
import (
	"log"
	"net/http"
	"time"
)

func MyMiddleware(h http.Handler) http.Handler {
	return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
		t := time.Now()
		h.ServeHTTP(w, r)
		d := time.Now().Sub(s).Milliseconds()
		log.Printf("end %s (%d ms)\n", t.Format(time.RFC3339), d)
	})
}
```