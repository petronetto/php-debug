
# PHP Debug container
## Running the Debug container

The Debug container is configured to run the file that bootstrap applications in folder `/var/www/html/public`, because I use Laravel by default, so, if you don't use a framework that bootstrap the application in this folder, you must put your source files there.
To the debug works, you must:

1) Set your local IP address in `XDEBUG_HOST` environment variable in`docker-compose.yml`.

2) Configure your editor/IDE to map the local source and the remote source.

Run:
```bash
docker-compose up -d
```

Optionaly you can build the container insteade use my build image, simply uncomment the `build` line in `docker-compose.yml` and run `docker-compose build`.

## IDE/Editor configuration

You need configure your editor/IDE to map the local source and where is the remote source.

### VS Code
To debug in VS Code, just put this config in your lauch.json:
```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "XDebug",
            "type": "php",
            "request": "launch",
            "port": 9000,
            // Path to your source in container
            "serverSourceRoot": "/var/www/html",
            // Path to your local source
            "localSourceRoot": "${workspaceRoot}/src"
        }
    ]
}
```

### PHPStorn
Configuration is in two parts:

#### 1:
Configuring a Server: `Preferences > Languages & Frameworks > PHP > Servers`

![](http://imagizer.imageshack.us/v2/1024x768q90/924/1ftWIS.png)



#### 2:
Configuring a new PHP Remote Debugger: `Run > Edit Configurations` click in `+` and `PHP Remote Debugger`
![](http://imagizer.imageshack.us/v2/1024x768q90/922/bnd7fq.png)


Enjoy!
