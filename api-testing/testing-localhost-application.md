# Testing localhost application

Testing your local environment before publishing the changes helps identifying bugs earlier and speeds up development cycle

## The problem

Sending a request from [Loadmill.com](http://loadmill.com/) to my localhost server is blocked.

When you try to reach localhost on your browser,  you are actually trying to connect to your local computer’s ip address, 127.0.0.1. This local IP address is the same for every computer. 

However, Loadmill is a SaaS \(software as a service\) company. That means that Loadmill’s web server runs on another computer somewhere in the world. Therefore, Loadmill.com will send an HTTP request to its own machine’s localhost ip address and not to your server, resulting in an error response. 

You can think of it this way: imagine you are on a vacation abroad, and you want to write a letter to your relatives back home. After you finished writing the letter, you would write on the envelope, “my home” as the target address. The mailman will not understand where to send the letter, of course. The mailman has his own idea of “my home”, but it is not your home, but rather, it’s his home. He will need your public home address in order to send the letter to your relatives. This scenario is equivalent to asking Loadmill \(the mailman\) to send an HTTP request \(the letter\) to localhost \(“my home”\).  


## The solution

We recommend using a public url service like [ngrock](https://ngrok.com/).

 Follow these instructions for a quick setup:

* Download and install [ngrock](https://ngrok.com/download)
* Run ngrok - execute the following command in a terminal \(assuming your application is using 3000 port\): 

  ```text
  ngrok http 3000
  ```

  or, If you’re server is running on HTTPS protocol:

  ```text
  ngrok http https://localhost:3000
  ```

* Copy the new public URL generated by ngrock:

![](../.gitbook/assets/image%20%281%29.png)

* Paste it in your Loadmill request url box:

![](https://lh6.googleusercontent.com/bZUmsu1EkgBNreOXqgz-cqDJMExB8e53IXCSQVB7cqCDgySDQ-clL_2MeDBLtWAVqAVpHwrT-ntrhZ-ntsKAwBWpgr_Wx67ooIPCsGLVrNOaolBa9kR4eQyw2wqmbo4izmoC4o9-)

And that's it! You are good to go.

