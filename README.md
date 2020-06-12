### Read Me First

##### 1. Format of the properties file
`{application}-{profile}.[yml|properties]`


Wherein: 

- `application`: the name of client application (1:1), as specified in client app by **spring.application.name** in bootstrap.[yml|properties]
- `profile` (optional): the profile the client application is currently running, as specified in client app by **spring.profiles.active** in bootstrap.[yml|properties]

##### 2. Where should I put the properties file?

Answer: Based on the config from server, specified in **spring.cloud.config.server.git.searchPaths**

If you want to specify general properties use for all application, we can add them to application.[yml|properties].



** @The rule of thumb:**

```
The config from more specific one will take prededence.
{application}-{profile}.[yml|properties] >  {application}.[yml|properties] > application.[yml|properties]
```


##### 3. The configuration is branch-sensitive, means client app/server can be configured to get config from specific branch

- **client app**: specified by *spring.cloud.config.server.git.default-label* in application.[yml|properties], effective when not specified in client app
- **server config**: specified by *spring.cloud.config.label* in bootstrap.[yml|properties], take precedence the value from the server config.