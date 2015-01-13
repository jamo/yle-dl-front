## CGI interface for yle-dl

[`yle-dl`](http://aajanki.github.io/yle-dl/) must be in `$PATH` of the process executing the `areenadl` GCI script

#### Deployment

This can be deployed as apache CGI script.  
Place `areenadl` from this repo to path pointed by `ScriptAlias`, e.g. to /opt/areenadl/

This uses `/tmp/areenadl/` for storing downloaded files it should be accessible by apache user.

```
<VirtualHost *:443>
  ServerName server.name

  ScriptAlias /get/ /opt/areenadl/

  DocumentRoot /tmp/areenadl/

  <Directory /opt/areenadl/>
    Require all granted
  </Directory>

</VirtualHost>
```

#### API

This provides following api

* /
> Show file listing provided by apache

* /:id
> Show file listing for folder with the name of :id

* /get/:id
> Downloads file with id :id with yle-dl

* /get/:id?delete=1
> If file with :id is downloaded, removes the folder with the name of :id




#### Disclaimer

Please keep in mind that this is not to be used to automatate downloading programs from yle-areena.

And running CGI scripts like this might create unknown security issues to the machine being used.

For deployment protection with at least http basic auth is recommended.

