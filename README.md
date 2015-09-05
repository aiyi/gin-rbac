## gin-rbac
gin-rbac is a Role-based access control (RBAC) middleware for Gin framework to filter out unauthorized REST API access.

## Concepts
##### Resource
An API endpoint. (for example: /api/projects/:id)
  
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

## Usage
Install the package
```
   $ go get github.com/aiyi/gin-rbac
```

Import the package
```
   import github.com/aiyi/gin-rbac
```

Use the middleware
Tbd

