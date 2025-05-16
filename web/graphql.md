---
description: GraphQL use the same endpoint for all requests
---

# GraphQL

## Possible endpoints

* `/graphql`
* `/api`
* `/api/graphql`
* `/graphql/api`
* `/graphql/graphql`

{% hint style="info" %}
Possiblity to add `/v1` to the path, sometimes works
{% endhint %}

## Universal queries

Sending `query{__typename}`  will include string `{"data": {"__typename": "query"}}` &#x20;



## Methods

Best practice for production is to only accept `POST` that have content-type `application/json` which helps protect against CSRF but some endpoints my accept other methods such as GET or POST with `x-www-form-urlencoded`&#x20;



## Schema field

Query the `__schema`&#x20;

```
{
    "query": "{__schema{queryType{name}}}"
}
```

If introspection is enabled, the response returns the names of all available queries.



## Full introspection query

```
 query IntrospectionQuery {
        __schema {
            queryType {
                name
            }
            mutationType {
                name
            }
            subscriptionType {
                name
            }
            types {
             ...FullType
            }
            directives {
                name
                description
                args {
                    ...InputValue
            }
            onOperation  #Often needs to be deleted to run query
            onFragment   #Often needs to be deleted to run query
            onField      #Often needs to be deleted to run query
            }
        }
    }

    fragment FullType on __Type {
        kind
        name
        description
        fields(includeDeprecated: true) {
            name
            description
            args {
                ...InputValue
            }
            type {
                ...TypeRef
            }
            isDeprecated
            deprecationReason
        }
        inputFields {
            ...InputValue
        }
        interfaces {
            ...TypeRef
        }
        enumValues(includeDeprecated: true) {
            name
            description
            isDeprecated
            deprecationReason
        }
        possibleTypes {
            ...TypeRef
        }
    }

    fragment InputValue on __InputValue {
        name
        description
        type {
            ...TypeRef
        }
        defaultValue
    }

    fragment TypeRef on __Type {
        kind
        name
        ofType {
            kind
            name
            ofType {
                kind
                name
                ofType {
                    kind
                    name
                }
            }
        }
    }
```

You can introspection on a visualizer:

{% embed url="https://graphql-kit.com/graphql-voyager/" %}

{% embed url="https://github.com/graphql-kit/graphql-voyager" %}
