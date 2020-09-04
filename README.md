# Interface Mesh

If you treat the APIs (interfaces) as 1st class citizens in your Service Mesh configuration, you get an Interface Mesh ;-)

## API Resource

**API Group:** stable.patricelabs.io

**Version:** v1alpha1

This resource is used to describe an _API_ using OpenAPI 2.0. It also contains metadata about the _API_.

```yaml
apiVersion: "stable.patricelabs.io/v1alpha1"
kind: API
metadata:
  name: alpha-api
spec:
  metadata:
    owner: Patrice
  swagger:
    info:
      title: Alhpa API
    host: acme-api
    paths:
      "/path-01":
        get:
          responses:
            "200":
              description: OK
```

## Microservice Resource

This resource is used to describe an _(micro)service_, as well as its _subscriptions_ to _API endpoint(s)_.

```yaml
apiVersion: "stable.patricelabs.io/v1alpha1"
kind: Microservice
metadata:
  name: client-x-service
spec:
  name: client-x
  subscriptions:
    - method: get
      host: acme-api
      pathTemplate: /path-01
```

## References

<https://github.com/OAI/OpenAPI-Specification/blob/master/schemas/v2.0/schema.json>
