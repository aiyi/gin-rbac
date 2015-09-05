## gin-rbac
gin-rbac is a role-based access control (RBAC) middleware for [Gin] framework to filter out unauthorized REST API access.

## Terms and concepts
##### Resource
Each resource is an API endpoint. (for example: /api/products/:id)

##### Operation
GET/PUT/DELETE/POST

##### Permission
Allow an operation on a specific resource.

##### User
Represents identity of a request to protected resources.

##### Role
Dynamic role: $everyone (for all users), $authenticated (authenticated users).

Static role: e.g. admin (a defined role for administrators), manager, etc.

##### User-Role / Role-Permission assignment
Users is connected with roles and roles are connected with permission (operation-resource) tuples with a n-to-n mapping.

##### Access control policy
policy.json:
```json
{
  "/api/products": {
    "GET" : ["$authenticated"]
  },

  "/api/products/:id": {
    "GET" : ["$authenticated"],
    "PUT" : ["manager", "editor"],
    "DELETE" : ["admin"]
  }
}
```

## Usage
Install the package
```sh
go get github.com/aiyi/gin-rbac
```

Use the middleware
```go
import (
    "github.com/gin-gonic/gin"
    "github.com/aiyi/gin-rbac"
)

func main() {
    g := gin.New()
    g.Use(rbac.Middleware("policy.json", func(c *gin.Context) *rbac.Roles {
        // write your custom code to return roles of current user
    }))

    g.GET("/api/products", func(c *gin.Context) {
        // handle GET products
    })

    g.DELETE("/api/products/:id", func(c *gin.Context) {
        // handle DELETE by product id
    })
}
```

[Gin]: http://gin-gonic.github.io/gin/
