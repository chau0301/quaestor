<div align="center">
<pre>
 ██████╗ ██╗   ██╗ █████╗ ███████╗███████╗████████╗  ██████╗ 
██╔═══██╗██║   ██║██╔══██╗██╔════╝██╔════╝╚══██╔══╝ ██╔═══██╗
██║   ██║██║   ██║███████║█████╗  ███████╗   ██║    ██║   ██║
██║▄▄ ██║██║   ██║██╔══██║██╔══╝  ╚════██║   ██║    ██║   ██║
╚██████╔╝╚██████╔╝██║  ██║███████╗███████║   ██║    ╚██████╔╝
 ╚══▀▀═╝  ╚═════╝ ╚═╝  ╚═╝╚══════╝╚══════╝   ╚═╝    ╚═══════╝
---------------------------------------------------
nestjs cli program to send requests
</pre>
</div>


Is it just me or is curl a little too complicated?
Want something simpler in life? something made for humans? Try quaestor -- A Nestjs program that reads a json/yml file for request data and sends the request

## Installation

npm install this repo.
(Note: Compatible with Node 16.x and above )

```sh
npm install quaestor
```

(or)

```sh
npm install quaestor
```

## Usage example

### To get help with commandline arguments

```sh
quaestor --help
```

### Using Command-line Arguments

```sh
quaestor -f "some/folder/myrequest.yml"
```

(or)

```sh
quaestor -f "some/folder/myrequest.json"
```

### Colorize Output

```sh
quaestor -f "some/folder/myrequest.yml" -c
```

### Disclaimer

sometimes the quaestor command doesn't work in windows if the package is installed globally.

to avoid this, install the package in a local virtual env

first, go to quaestor repository

```sh
yarn install -g npm
```

Install quaestor:

```sh
npm install
```

and then npm run. But you will have to activate that env everytime you want to use quaestor.

## IO Redirection

the response is written to stdout and headers/status are written to stderr so that users can take IO redirection to their advantage. This works on windows, linux and mac.

```sh
quaestor -f "some/folder/myrequest.yml" > res.json 2> res_headers.txt
```

both stdout and stderr can be redirected to the same file

```sh
quaestor -f "some/folder/myrequest.yml" > res.txt 2>&1
```

## Sample request file (`myrequest.yml`)

### GET

```yaml
url: https://cdn.animenewsnetwork.com/encyclopedia/api.xml?anime=4658
method: get
params:
  offset: 2
  limit: 100
headers:
  accept: text/xml
  accept-language: en
timeout: 5000
```

#### File Download (`quaestor -f "some/folder/myrequest.yml" > book.pdf`)

```yaml
url: http://do1.dr-chuck.com/pythonlearn/EN_us/pythonlearn.pdf
method: get
```

### POST

```yaml
url: https://jsonplaceholder.typicode.com/todos/
method: POST
headers:
  Authorization: Basic bXl1c2VybmFtZTpteXBhc3N3b3Jk
  content-type: application/json
data:
  title: walk the dog
  completed: false
timeout: 5000
```

### PUT

```yaml
url: https://jsonplaceholder.typicode.com/todos/1
method: PUT
headers:
  content-type: application/json
data:
  title: walk the dog
  completed: true
timeout: 5000
```

### DELETE

```yaml
url: https://jsonplaceholder.typicode.com/todos/1
method: DELETE
```

## Complete request file with all available fields (`myrequest.yml`)

```yaml
method: XXX # (REQUIRED) GET, OPTIONS, HEAD, POST, PUT, PATCH, or DELETE
url: XXX # (REQUIRED) must be prefixed with http:// or https://

params: # url query parameters. have as many as you like
  offset: 0
  limit: 10

data: # data for POST
  name: john
  age: 22
  hobbies:
    - running
    - eating
    - sleeping

# you can also type data in json format instead of yaml
data: |
  {
    "name": "john",
    "age": 22,
    "hobbies": ["running", "eating", "sleeping"]
  }

headers: # have as many as you like
  Content-Type: application/json
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c


cookies: # have as many as you like
  mycookie: cookievalue
  myothercookie: othercookievalue

timeout: 3.14 # seconds

allow_redirects: true # true or false

proxies: # have as many as you like
  http: http://10.10.1.10:3128
  https: https://10.10.1.11:1080
  ftp: ftp://10.10.1.10:3128

# EITHER verify server's TLS certificate. true or false
verify: true
# OR path to a CA bundle to use
verify: some/folder/cacert.crt

# EITHER path to single ssl client cert file (*.pem)
cert: some/folder/client.pem
# OR (*.cert), (*.key) pair.
cert:
  - some/folder/client.cert
  - some/folder/client.key

```

## Development setup

Clone this repo and install packages listed in requirements.txt

Windows:
```sh
copy .env .env.example
```

Unix/Linux:
```sh
cp .env .env.example
```

## Meta

M. Zahash – zahash.z@gmail.com

Distributed under the MIT license. See `LICENSE` for more information.

[https://github.com/zahash/](https://github.com/zahash/)

## Contributing

1. Fork it (<https://github.com/chau0301/quaestor/fork>)
2. Create your feature branch (`git checkout -b feature/fooBar`)
3. Commit your changes (`git commit -am 'Add some fooBar'`)
4. Push to the branch (`git push origin feature/fooBar`)
5. Create a new Pull Request
