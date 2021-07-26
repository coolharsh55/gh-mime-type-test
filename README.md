# Testing Github Pages for RDF/Turtle Content Negotiation

Files are stored in root. Outcome: no content negotiation.

```bash
$harsh@XNMAM1:gh-mime-type-test >curl -L -I -s -X GET https://harshp.com/gh-mime-type-test -H "Accept: text/html" | grep "content-type"
content-type: text/html
content-type: text/html; charset=utf-8
$harsh@XNMAM1:gh-mime-type-test >curl -L -I -s -X GET https://harshp.com/gh-mime-type-test -H "Accept: text/turtle" | grep "content-type"
content-type: text/html
content-type: text/html; charset=utf-8
$harsh@XNMAM1:gh-mime-type-test >curl -L -I -s -X GET https://harshp.com/gh-mime-type-test/ -H "Accept: text/turtle" | grep "content-type"
content-type: text/html; charset=utf-8
$harsh@XNMAM1:gh-mime-type-test >curl -L -I -s -X GET https://harshp.com/gh-mime-type-test/index -H "Accept: text/turtle" | grep "content-type"
content-type: text/html; charset=utf-8
$harsh@XNMAM1:gh-mime-type-test >curl -L -I -s -X GET https://harshp.com/gh-mime-type-test/index.ttl -H "Accept: text/turtle" | grep "content-type"
content-type: text/turtle; charset=utf-8
```

Files are stored as subfolder. Outcome: no content negotiation.

```bash
$harsh@XNMAM1:gh-mime-type-test >curl -L -I -s -X GET https://harshp.com/gh-mime-type-test/sub -H "Accept: text/turtle" | grep "content-type"
content-type: text/html
content-type: text/html; charset=utf-8
$harsh@XNMAM1:gh-mime-type-test >curl -L -I -s -X GET https://harshp.com/gh-mime-type-test/sub/ -H "Accept: text/turtle" | grep "content-type"
content-type: text/html; charset=utf-8
$harsh@XNMAM1:gh-mime-type-test >curl -L -I -s -X GET https://harshp.com/gh-mime-type-test/sub/index -H "Accept: text/turtle" | grep "content-type"
content-type: text/html; charset=utf-8
$harsh@XNMAM1:gh-mime-type-test >curl -L -I -s -X GET https://harshp.com/gh-mime-type-test/sub/index.ttl -H "Accept: text/turtle" | grep "content-type"
content-type: text/turtle; charset=utf-8
$harsh@XNMAM1:gh-mime-type-test >curl -L -I -s -X GET https://harshp.com/gh-mime-type-test/sub/index.ttl -H "Accept: text/html" | grep "content-type"
content-type: text/turtle; charset=utf-8
```