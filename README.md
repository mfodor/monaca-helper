# monaca-helper
Helper script for Monaca development

## Setup

### 1. Export your monaca server root path to `PATH_MONACA_SERVER` in your `.bash_profile` or `.bashrc`

```bash
# add to your bash profile file
export PATH_MONACA_SERVER="/path/to/monaca"
```

### 2. Make sure the file is executable

```bash
# in monaca-helper folder
chmod +x monaca
```

### 3. Add the script to your $PATH

```bash
ln -s /path/to/monaca-helper/monaca /usr/local/bin/monaca

# in monaca-helper folder
ln -s monaca /usr/local/bin/monaca
```

## Usage

```
monaca <command> [params]
```

Run the script without any params to get the usage info.

```bash
monaca
# this will print usage info
```

## Commands

### home                 

Print Monaca server directory. You can use this to check if the server root is
configured correctly. Or to manually `cd` to server root.

```bash
cd $(monaca home)
```

### cd

Go to Monaca dir. If you run it without sourcing the command it will not take
effect because the script is run in separate shell.

```bash
# notice the dot before the command
. monaca cd
```

### u|up|start

Start Monaca ecosystem. It will call `docker-compose up -d` in server root.

### d|down|stop

Stop Monaca ecosystem.  It will call `docker-compose down` in server root.

### r|restart

Restart Monaca ecosystem

### rf|restart-frontend

Restart monaca-frontend container

### c|reconfigure

Stop Monaca ecosystem, run configure then start

### pull

Do a pull in Monaca server and in each installed app

### build|packager

Stop Monaca ecosystem, reconfigure then build docker images with packager.

#### Option: up

Start Monaca ecosystem after image build finished.

```bash
monaca build up
```

### cc|cache

Clear/Rebuild cache in web-server (`/data/monaca.mobi/symfony cc`)

### debug

Install XDebug into web-server.

#### Option: out

If out is passed xdebug will be configured to be accessible outside of the
docker container. (e.g. in your IDE)

### run

Run command in web-server with bash (only $1)

```bash
# for example
monaca run 'cd monaca.mobi; cat a-file.ext'
```
