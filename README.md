This is the end point the request is sending the data to (its in the server.js file of the backend api Udacity supplied us with). It's expecting the request's body object to have an 'option' key.

```js
  app.post('/comments/:id', bodyParser.json(), (req, res) => {
      const { option } = req.body
      comments.vote(req.token, req.params.id, option)
        .then(
            (data) => res.send(data),
            (error) => {
                console.error(error)
                res.status(500).send({
                    error: 'There was an error.'
                })
            }
        )
})
```

In the headers you need the Content-Type property that tells the server the data content is in JSON format.

```js

  state = {
    myHeaders: {
      'Authorization': 'esats server',
      'Content-Type': 'application/json',
    },
    api: 'http://localhost:5001'
  }

```

Also the data your sending to the server needs to be in JSON format

```js
  incrementCommentScore (id) {

    ...

    let params = {
      method: 'POST',
      headers: myHeaders,
      body: JSON.stringify({ option: 'upVote' }),
    }
  }
```

sources:

https://stackoverflow.com/questions/9254891/what-does-content-type-application-json-charset-utf-8-really-mean

https://stackoverflow.com/questions/20226169/how-to-pass-json-post-data-to-web-api-method-as-object
