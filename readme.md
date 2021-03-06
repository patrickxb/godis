# godis

godis - a [Redis](http://redis.io) client for Go. It supports all Redis commands
and common features such as pipelines and pubsub.

1. [Readme](http://susr.org/godis/)
2. [Package docs](http://susr.org/godis/pkg/)
3. [Source code](https://github.com/simonz05/godis)

## Install godis

godis is available at github.com. Get it by running.

    $ git clone git://github.com/simonz05/godis.git

And now compile and install it with one command.

    $ make install

Importing godis to your code can be done with `import "godis"`. Thats it!

## Use godis

Running git clone also checks out some examples into the `examples` directory.
Here is the code for the SET/GET example.

    package main

    import (
        "godis"
        "fmt"
    )

    func main() {
        // new client on default port 6379, select db 0 and use no password
        c := godis.New("tcp:127.0.0.1:6379", 0, "") 

        // set the key "foo" to "Hello Redis"
        c.Set("foo", "Hello Redis")

        // retrieve the value of "foo". Returns an Elem obj
        elem, _ := c.Get("foo")

        // convert the obj to a string and print it 
        fmt.Println("foo: ", elem.String())
    }

Build the examples. 

    $ make 

To run it we type.

    $ ./string
    foo: Hello Redis

In case your redis server isn't running the output looks like this.

    $ ./string 
    Connection error 127.0.0.1:6379

## TODO

  * Add tests server commands.
  * Implement transactions.
  * Pipeline need more testing.
  * MULTI/EXEC.

## Acknowledgment

The work on this client started as I was hacking around on Michael Hoisie's
original redis client for Go. Also the recent work done by Frank Müller on his
client gave me some pointers how to better handle return values. 
