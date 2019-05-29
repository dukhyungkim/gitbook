---
description: Board API
---

# board-api

{% api-method method="get" host="https://board-api" path="/api/v1/articles" %}
{% api-method-summary %}
Get all articles
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to get an array of articles.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Articles successfully retrieved.
{% endapi-method-response-example-description %}

```javascript
{
  "data": [
    {
      "type": "articles",
      "id": "1",
      "attributes": {
        "title": "Initial Article",
        "body": "This is content of article"
      },
      "links": {
        "self": "https://board-api/api/v1/articles/1"
      }
    },
    {
      "type": "articles",
      "id": "1",
      "attributes": {
        "title": "Initial Article",
        "body": "This is content of article"
      },
      "links": {
        "self": "https://board-api/api/v1/articles/1"
      }
    }
  ]
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=204 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "data": []
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://board-api" path="/api/v1/articles/:id" %}
{% api-method-summary %}
Get an article  
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to get an article.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="integer" required=true %}
article id
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
An article successfully retrieved.
{% endapi-method-response-example-description %}

```javascript
{
  "data": {
    "type": "articles",
    "id": "1",
    "attributes": {
      "title": "Initial Article",
      "body": "This is content of article"
    },
    "links": {
      "self": "https://board-api/api/v1/articles/1"
    }
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "errors": {
      "status": "404",
      "source": {
          "pointer": "/data/type/articles/1"
      },
      "title":  "Not Found",
      "detail": "The article id 1 is not found."
  }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://board-api" path="/api/v1/articles" %}
{% api-method-summary %}
Post an article
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to post an article
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="title" type="string" required=true %}
the title of article
{% endapi-method-parameter %}

{% api-method-parameter name="body" type="string" required=true %}
the contents of article
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=201 %}
{% api-method-response-example-description %}
Articles successfully retrieved.
{% endapi-method-response-example-description %}

```javascript
{
  "data": {
    "type": "articles",
    "id": "1",
    "attributes": {
      "title": "Initial Page"
    },
    "links": {
      "self": "https://board-api/api/v1/articles/1"
    }
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "errors": {
      "status": "500",
      "source": {
          "pointer": "/data/type/articles/1"
      },
      "title":  "Internal Server Error",
      "detail": "Can't save the article to database."
  }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Template of POST request body

```javascript
{
  "data": {
    "type": "articles",
    "attributes": {
      "title": "Initial Article",
      "body": "This is content of article"
    }
  }
}
```

{% api-method method="put" host="https://board-api" path="/api/v1/articles/:id" %}
{% api-method-summary %}
Edit an article
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to edit an article
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="integer" required=true %}
article id
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="title" type="string" required=false %}
the title of article to change
{% endapi-method-parameter %}

{% api-method-parameter name="body" type="string" required=false %}
the body of article to change
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "data": {
    "type": "articles",
    "id": "1",
    "attributes": {
      "title": "Initial Article",
      "body": "This is modifed content of article"
    },
    "links": {
      "self": "https://board-api/api/v1/articles/1"
    }
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "errors": {
      "status": "404",
      "source": {
          "pointer": "/data/type/articles/1"
      },
      "title":  "Not Found",
      "detail": "The article id 1 is not found."
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "errors": {
      "status": "500",
      "source": {
          "pointer": "/data/type/articles/1"
      },
      "title":  "Internal Server Error",
      "detail": "Can't update the article to database."
  }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Template of PUT request body

```javascript
{
  "data": {
    "type": "articles",
    "id": "1",
    "attributes": {
      "title": "Initial Article",
      "body": "This is modified content of article"
    },
    "links": {
      "self": "https://board-api/api/v1/articles/1"
    }
  }
}
```

{% api-method method="delete" host="https://board-api" path="/api/v1/articles/:id" %}
{% api-method-summary %}
Delete an article
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to delete an article
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="integer" required=true %}
article id
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript

```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "errors": {
      "status": "404",
      "source": {
          "pointer": "/data/type/articles/1"
      },
      "title":  "Not Found",
      "detail": "The article id 1 is not found."
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "errors": {
      "status": "500",
      "source": {
          "pointer": "/data/type/articles/1"
      },
      "title":  "Internal Server Error",
      "detail": "Can't update the article to database."
  }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

