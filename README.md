# Tayler

Tayler is a log tailing implementation forked from [Apache Commons IO](http://commons.apache.org/io/), providing improved performances, bug fixes, cleaner APIs and a
codebase which will be actively maintained and developed :)

## Usage

First, you need to implement the _tayler.TailerListener_ or _tayler.TailerListenerAdapter_, providing an implementation for the following API methods:

* init: called on listener initialization.
* handle: called at each line handling.
* fileNotFound: called if the tailed file is not found.
* fileRotated: called if the tailed file is rotated.
* error: called in case of tail/handling errors.
* stop: called after stopping tailer.

Then, you just create a _tayler.Tailer_ object by specifying the following constructor arguments:

* file: the log file to tail.
* listener: the previously implemented listener.
* delay: the tail delay time, in milliseconds.
* end: a boolean specifying if tailing from start or end of file.
* bufferSize: the size of the buffer for buffered reads, in bytes.

The _tayler.Tailer_ object is indeed a Runnable, so the final step is to start a thread or submit it to an executor in order to actually start tailing.
That's it.

## Download

Tayler is a self-contained jar you can download from the Downloads section above.

If you're a Maven user, you can also configure Tayler on your project by importing the Clojars repository:

    <repository>
        <id>clojars.org</id>
        <url>http://clojars.org/repo</url>
    </repository>

And then declaring the dependency:

    <dependency>
        <groupId>tayler</groupId>
       <artifactId>tayler</artifactId>
       <version>1.1</version>
    </dependency>

## Feedback

Contact me on [twitter](http://twitter.com/sbtourist).

## License

Distributed under the [Apache Software License](http://www.apache.org/licenses/LICENSE-2.0.html).
