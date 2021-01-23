# Quick Break down of basic puppet manifest (.pp files)

[jleskinen notes](https://jussinotes.wordpress.com/2013/04/01/learning-puppet-1-hello-world/)

[digital ocean tutorial](https://www.digitalocean.com/community/tutorials/getting-started-with-puppet-code-manifests-and-modules)

[Youtube usage](https://www.youtube.com/watch?v=1jySLtutfRc)

`~$ cat` short for concatenate
___

### Installation

After accessing a fresh VM/Server, you will need to update the server, then install puppet

`sudo apt-get update`

`sudo apt-get install puppet`

___

### Usage

A mock puppet manifest may look like this

```
~$ vi var/library/puppet_hello/sayhello.pp
```

sayhello.pp file:

```
file {'var/library/puppet_hello/mock_text.rtf':
  content => "Hello Puppet\n",
}
```

This will execute the commands in the .pp file

`puppet apply var/library/puppet_hello/sayhello.pp`

To view the response

`~$ cat /var/library/puppet_hello/mock_text.rtf`

