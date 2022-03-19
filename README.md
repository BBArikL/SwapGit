# SwapGit

Swapgit lets you swap git configs easily in a shared development environment.

## Usage

Lets say that you want to set up a common remote working machine for you and your team. Normally you would need to set up every account with the ssh keys, gpg keys and so on.

Each person would then need to reveal these informations to everyone. With SwapGit, you can swap between users easily.

### Setup:

#### With existing files:
```
$ swapgit -n -u User1 -p YOUR-PASSWORD -f ~/.gitconfig ~/.ssh/id_private_key
```

#### Same, but interactively:
```
$ swapgit -ni
Enter the user name: User1
Enter the password: YOUR-PASSWORD
```

#### With a template:
```
$ swapgit -ni --basic # DEFAULT: Basic .gitconfig
$ swapgit -ni --secure # .gitconfig, ssh keys and GPG keys
```

#### With a custom installation:
```
$ swapgit -ni --ssh --gpg --pretty # Adds ssh keys, gpg keys and pretty commands (aliases for log, commit, etc.)
```

### Usage:
```
$ git config -l
$ swapgit --swap User1
Enter password for User1: YOUR-PASSWORD
Swapping Done!
$ git config -l
user.name=User1
user.email=user1@user-email.com
.....
```

#### To save a new config when logged in as a user:
```
$ swapgit --save
All files saved!
```

#### To log out:
```
$ swapgit --logout # This will get rid of the user-specific files  
```

The program works by swapping out specified files when logging in and out of a git profile. All profiles are secured by the user's password.
