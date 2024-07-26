# Quote-API

Quote-API is a simple and efficient API designed to provide quotes from various authors. Built with Express and Node.js, it allows users to retrieve quotes based on specific parameters and offers easy integration into different applications.

## Features

- Retrieve random quotes
- Get quotes by specific authors
- Add new quotes

## Getting Started

### Installation

1. Clone the repository:

    ```bash
    git clone https://github.com/BrayanCordero/Quote-API.git
    cd Quote-API
    ```

2. Install the required packages:

    ```bash
    npm install
    ```


### Running the API

To start the API server, run:

    ```bash
    node server.js

## Usage

### Endpoints

#### Get a random quote

    ```http
    GET /api/quotes/random
    ```

Example:

    ```bash
    curl http://127.0.0.1:5000/api/quotes/random
    ```

#### Get quotes (optionally filter by author)

    ```http
    GET /api/quotes
    ```

Example:

    ```bash
    curl http://127.0.0.1:5000/api/quotes?person=Mark%20Twain
    ```

#### Add a new quote

    ```http
    POST /api/quotes
    ```

Example:

    ```bash
    curl -X POST "http://127.0.0.1:5000/api/quotes?quote=The%20only%20limit%20to%20our%20realization%20of%20tomorrow%20is%20our%20doubts%20of%20today.&person=Franklin%20D.%20Roosevelt"
    ```

### Endpoint Definitions

#### Get a random quote

    ```javascript
    app.get('/api/quotes/random', (req, res, next) => {
        const randomQuote = {
            quote: getRandomElement(quotes) 
        }
        res.send(randomQuote)
    })
    ```

#### Get quotes (optionally filter by author)

    ```javascript
    app.get('/api/quotes', (req, res, next) => {
        const person = req.query.person
        if (person) {
            const personQuotes = quotes.filter(quote => quote.person === person)
            res.send({ quotes: personQuotes })
        } else {
            res.send({ quotes: quotes })
        }
    })
    ```

#### Add a new quote

    ```javascript
    app.post('/api/quotes', (req, res, next) => {
        const quote = req.query.quote
        const person = req.query.person
        if (quote && person) {
            const newQuote = {
                quote: quote,
                person: person
            }
            quotes.push(newQuote)
            res.send({ quote: newQuote })
        } else {
            res.status(400).send()
        }
    })
    ```

