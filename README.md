Gokogiri
========
[![Build Status](https://travis-ci.org/quinn-lima/gokogiri.svg?branch=master)](https://travis-ci.org/quinn-lima/gokogiri)
[![codecov](https://codecov.io/gh/quinn-lima/gokogiri/branch/master/graph/badge.svg)](https://codecov.io/gh/quinn-lima/gokogiri)
[![Go Report Card](https://goreportcard.com/badge/github.com/quinn-lima/gokogiri)](https://goreportcard.com/report/github.com/quinn-lima/gokogiri)
[![GoDoc](https://godoc.org/github.com/quinn-lima/gokogiri?status.svg)](https://godoc.org/github.com/quinn-lima/gokogiri)

LibXML bindings for the Go programming language.
------------------------------------------------
The gokogiri package provides a Go interface to the libxml2 library.

It is inspired by the ruby-based Nokogiri API, and allows one to parse, manipulate, and create HTML and XML documents. Nodes can be selected using either CSS selectors (in much the same fashion as jQuery) or XPath 1.0 expressions, and a simple DOM-like interface allows for building up documents from scratch.

It uses parsing default options that ignore errors or warnings, making it suitable for the poorly-formed 'tag soup' often found on the web. The xml.StrictParsingOption is conveniently provided for standards-compliant behaviour.

This fork incorporates changes required to compile on Go 1.4 and above.

To install:

- sudo apt-get install libxml2-dev libonig-dev
- go get github.com/quinn-lima/gokogiri

To run test:

- go test github.com/quinn-lima/gokogiri/html
- go test github.com/quinn-lima/gokogiri/xml

Basic example:

    package main

    import (
      "io"
      "net/http"

      "github.com/quinn-lima/gokogiri"
    )

    func main() {
      // fetch and read a web page
      resp, _ := http.Get("http://www.google.com")
      page, _ := io.ReadAll(resp.Body)

      // parse the web page
      doc, _ := gokogiri.ParseHtml(page)
      defer doc.Free()

      // perform operations on the parsed page -- consult the tests for examples
    }

Original upstream version by Zhigang Chen and Hampton Catlin.
