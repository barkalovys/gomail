# Gomail
[![Build Status](https://travis-ci.org/go-gomail/gomail.svg?branch=v2)](https://travis-ci.org/go-gomail/gomail) [![Code Coverage](http://gocover.io/_badge/gopkg.in/gomail.v2)](http://gocover.io/gopkg.in/gomail.v2) [![Documentation](https://godoc.org/gopkg.in/gomail.v2?status.svg)](https://godoc.org/gopkg.in/gomail.v2)

## Introduction

Fork of https://github.com/go-gomail/gomail


## Features

Gomail supports:
- Attachments
- Embedded images
- HTML and text templates
- Automatic encoding of special characters
- SSL and TLS
- Sending multiple emails with the same SMTP connection


## Documentation

https://godoc.org/gopkg.in/gomail.v2


## Download

    go get gopkg.in/gomail.v2


## Examples

See the [examples in the documentation](https://godoc.org/gopkg.in/gomail.v2#example-package).


## FAQ

### x509: certificate signed by unknown authority

If you get this error it means the certificate used by the SMTP server is not
considered valid by the client running Gomail. As a quick workaround you can
bypass the verification of the server's certificate chain and host name by using
`SetTLSConfig`:

    package main

    import (
    	"crypto/tls"

    	"gopkg.in/gomail.v2"
    )

    func main() {
    	d := gomail.NewDialer("smtp.example.com", 587, "user", "123456")
    	d.TLSConfig = &tls.Config{InsecureSkipVerify: true}

        // Send emails using d.
    }

Note, however, that this is insecure and should not be used in production.


## Contribute

Contributions are more than welcome! See [CONTRIBUTING.md](CONTRIBUTING.md) for
more info.


## Change log

See [CHANGELOG.md](CHANGELOG.md).


## License

[MIT](LICENSE)


## Contact

You can ask questions on the [Gomail
thread](https://groups.google.com/d/topic/golang-nuts/jMxZHzvvEVg/discussion)
in the Go mailing-list.
