# forward-shell

This is a method I had come up with after countless hours of trying to get [PentestMonkey: PHP FindSock Shell](http://pentestmonkey.net/tools/web-shells/php-findsock-shell) working some years ago.  This solution creates a shell that accepts commands via a Named Pipe (mkfifo) and outputs the results to a file.  By doing this the shell does not require a persistent network connection so you can establish a proper PTY behind a firewall that has egress ingress filtering to block reverse/bind shells.  It is best explained in my [Sokar Video](https://www.youtube.com/watch?v=k6ri-LFWEj4).

# Usage

There are two to three parts you need to modify to get this working, all parts have "MODIFY THIS" in the comments.
* IP Address within the WebShell.__init__ function.  This is the target
* payload in the WebShell.RunRawCmd - If you need to do anything special to format the command, for example place it in a serialized format for deserialization attacks.
* headers in WebShell.RunRawCmd -- This is how the exploit gets sent to the server, right now its hard coded for shell-shock. If you want to send it in a GET use PARAMS, POST use DATA, etc.  
If you are confused on how to edit this, I've done it quite a few times.  Just go to https://ippsec.rocks and search for forward shell to find videos.

# Future

I do not plan on making too many updates to this right now.  There's a key functionality missing which is required to do the machine i created in HackTheBox's Offshore lab.  It requires some critical thinking to implement/debug, so adding all of that robs many people of the learning experience that isn't technically hard but requires some proper planning.
