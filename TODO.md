
Tool And Config Requirement

###### Cygwin + Conemu / Terminal (For window user only) And configure bash shell environment

Install cygwin with the programs: vim, git, openssh, tmux, more, dos2unix, python3

Configure ssh(Mandatory):

  ```
  ssh-keygen -t rsa -b 4096 -C "yourmail"
  ```

Config git(Mandatory)

  edit ~/.ssh/config and make sure 

  ```
  Host gitlab.ahaysoft.com
  Preferredauthentications publickey
  Port 30522
  IdentityFile ~/.ssh/id_rsa
  ```

Configure ~/.bash_profile (Mandatory)

  ```
  export AHAYSOFT_DIR="/cygdrive/c/ahaysoft"
  export WIN_AHAYSOFT_DIR="c:/ahaysoft"
  export TERM=xterm-256color

  export JAVA_HOME="$AHAYSOFT_DIR/tools/jdk-14.0.2"
  export GRADLE_HOME="$AHAYSOFT_DIR/tools/gradle-6.6.1"
  export GRADLE_USER_HOME="$WIN_AHAYSOFT_DIR/tools/gradle-working"
#Increase memory for nodejs
  export NODE_OPTIONS=--max_old_space_size=4096

  PATH=$PATH:$JAVA_HOME/bin:$GRADLE_HOME/bin

  alias ls='ls --color'

  ```

###### Install nodejs and npm, pnpm

###### JDK 15 or above +  gradle 7

###### Spring Tools 4 Or Intellij IDE
  Install the lombok 
  ```sh
  $ java -jar lombok.jar
  ```
  Press the Specify Location button.
  Note: for Mac, go to the Contents directory within the .app file and find the STS.ini file, 
  it could be SpringToolSuite4.ini too.

###### VS Code (Not Visual Studio)

###### Postgres Server
Download and install database postgres server(install server, pgadmin, client)

###### DBeaver - Database Tool to explore a database and table relations

## Other Tools

## Setup configurations for  Spring Tool Suite / Eclipse before start coding
  [Download template format here](https://gitlab.ahaysoft.com/root/openfreightone/-/tree/develop/docs/eclipse)
### 1. Config
#### First, auto format when saving code

  1. Open Preferences
  2. Search "save" on search box
  3. Click "Save Actions" in "Java > Editor > Save Actions"
  4. Select all options below
  ```
  * Perform the selected on save
  * Format source code
  * Format edited line
  ```

#### Second, Import templates
##### Cleanup
  1. Open Preferences
  2. Choose "Java > Code Style > Clean Up"
  3. Choose "Import" and select the "ahaysoft-cleanup.xml"
  4. Apply

##### Formatter
  1. Open Preferences
  2. Choose "Java > Code Style > Formatter"
  3. Choose "Import" and select the "ahaysoft-formatter.xml"
  4. Apply

#### Third, Enable whitespace character
  1. Open Preferences
  2. Choose "General > Editors > Text Editor"
  3. Enable option "Show whitespace character"
  4. Apply

### 2. Install plugin
#### Eclemma: Show code coverage for Unit Test
  1. Open "Eclipse > Eclipse Marketplace"
  2. Find "Eclemma"
  3. Install this plugin
  4. Restart Eclipse

##Git

  ```
  Run                                                   

  git config --global user.email "you@example.com"    
  git config --global user.name "Your Name"           
  git config core.filemode false
#Line ending with unix style
  git config --global core.autocrlf false
  ```
  Quick rollback

  ```
  git checkout -- .
  ```

  Rollback to Head
  ```
$ git reset --hard HEAD       (going back to HEAD)

$ git reset --hard HEAD^      (going back to the commit before HEAD)
  $ git reset --hard HEAD~1     (equivalent to "^")

$ git reset --hard HEAD~2     (going back two commits before HEAD)
  ```

##Postgres DB

  Useful commands:

  ```
  createuser -U pgadmin  ofone
  dropuser   -U pgadmin  ofone
  psql -U pgadmin  -c "ALTER USER ofone WITH ENCRYPTED PASSWORD 'ofone'"

  psql -U pgadmin  -c 'CREATE DATABASE ofonedb'
  psql -U pgadmin  -c 'DROP   DATABASE ofonedb'

  psql -U pgadmin -c 'GRANT ALL PRIVILEGES ON DATABASE ofonedb TO ofone'
  ```


