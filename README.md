# Go fastcgi client

Copied from here https://code.google.com/archive/p/go-fastcgi-client/

## Download

    go get github.com/tdaugaard/go-fastcgi-client

## Example

```golang
func main() {
    reqParams := "name=value"
    env := make(map[string]string)
    env["REQUEST_METHOD"] = "GET"
    env["SCRIPT_FILENAME"] = "/var/www/html/test.php"
    env["SERVER_SOFTWARE"] = "go / fcgiclient "
    env["REMOTE_ADDR"] = "127.0.0.1"
    env["SERVER_PROTOCOL"] = "HTTP/1.1"
    env["QUERY_STRING"] = reqParams

    fcgi, err := fcgiclient.New("127.0.0.1", 9000)
    if err != nil {
        fmt.Printf("err: %v", err)
    }

    content, err := fcgi.Request(env, reqParams)
    if err != nil {
        fmt.Printf("err: %v", err)
    }

    fmt.Printf("content: %s", content)
}
```

## License

Original project was under the [New BSD License](http://opensource.org/licenses/BSD-3-Clause) and naturally so is this.