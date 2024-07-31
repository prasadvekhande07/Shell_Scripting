# Shell_Scripting
### Bash Scripting Summary

#### Storing Output of a Command in a Variable
```bash
variable_name=$(command)
```

#### Example Script
```bash
#!/bin/bash

echo "Setup and configure server"

file_name=config-yaml

if [ -d "config" ]; then
    echo "Reading config directory contents"
    config_files=$(ls config)
else
    echo "Config directory not found. Creating one"
    mkdir config
fi

echo "Using file $file_name to configure something"
echo "Here are all configuration files: $config_files"
```

#### File Test Operators
- `-d file`: Checks if file is a directory.
- `-f file`: Checks if file is a regular file.
- `-r file`: Checks if file is readable.
- `-w file`: Checks if file is writable.
- `-x file`: Checks if file is executable.

#### Relational Operators
- `-eq`: Checks if two numbers are equal.
- `-ne`: Checks if two numbers are not equal.
- `-gt`: Checks if the left number is greater than the right number.
- `-lt`: Checks if the left number is less than the right number.
- `-ge`: Checks if the left number is greater than or equal to the right number.
- `-le`: Checks if the left number is less than or equal to the right number.

#### String Operators
- `==`: Checks if two strings are equal.
- `!=`: Checks if two strings are not equal.
- `-z`: Checks if the string length is zero.
- `-n`: Checks if the string length is non-zero.

#### Example Conditional Script
```bash
#!/bin/bash

user_group=xx

if [ "$user_group" == "nana" ]; then
    echo "Configure the server"
elif [ "$user_group" == "admin" ]; then
    echo "Administer the server"
else
    echo "No permission to configure server. Wrong user group"
fi
```

#### Positional Parameters
```bash
#!/bin/bash

user_group=$1

if [ "$user_group" == "nana" ]; then
    echo "Configure the server"
elif [ "$user_group" == "admin" ]; then
    echo "Administer the server"
else
    echo "No permission to configure server. Wrong user group"
fi
```

#### Read User Input
```bash
#!/bin/bash

echo "Reading user input"
read -p "Please enter your password: " user_pwd
echo "Thanks for your password $user_pwd"
```

#### For Loop Example
```bash
#!/bin/bash

for param in "$@"; do
    if [ -d "$param" ]; then
        echo "Executing scripts in the config folder"
        ls -1 "$param"
    fi
    echo $param
done
```

#### While Loop Example
```bash
#!/bin/bash

sum=0
while true; do
    read -p "Enter a score: " score
    if [[ $score == "q" ]]; then
        break
    fi
    sum=$((sum + score))
    echo "Total score: $sum"
done
```

#### Functions Example
```bash
#!/bin/bash

function score_sum {
    sum=0
    while true; do
        read -p "Enter a score: " score
        if [[ $score == "q" ]]; then
            break
        fi
        sum=$((sum + score))
        echo "Total score: $sum"
    done
}

score_sum
```

#### Environment Variables
- Print all environment variables: `printenv`
- Print specific environment variable: `printenv USER`
- Set an environment variable: `export DB_USERNAME=dbuser`
- Delete an environment variable: `unset DB_NAME`

### Persisting Environment Variables
- **User-specific**: Add to `~/.bashrc`
- **System-wide**: Add to `/etc/environment`

### Adding Custom Commands
- Add a script to your PATH by modifying `.bashrc`
- Example:
  ```bash
  vim welcome
  #!/bin/bash
  echo "Welcome to DevOps Bootcamp $USER"
  chmod a+x welcome
  vim .bashrc
  PATH=$PATH:/path/to/your/script
  source .bashrc
  ```

This guide covers the basics of bash scripting, including conditionals, loops, functions, and environment variables. It should serve as a solid foundation for more complex scripts and automation tasks.
