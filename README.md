# git-commit-msg-hook

# Setup
## AI server
Get the huggingface-cli via brew:
```
brew install huggingface-cli
```

Add your account token by logging in and generating one, then run and enter it:
```
huggingface-cli login
```

Download an mlx-community model from huggingface like:
```
huggingface-cli download mlx-community/phi-4-4bit
```

Create a new pyenv somewhere like:
```
python -m venv <venv_name>
```

This will create a directory named `<venv_name>`, after you want to activate it:
```
source <venv_name>/bin/activate
```

Install mlx_lm:
```
pip intall mlx_lm
```

Serve it over an open ai compat server, using mlx:
```
mlx_lm.server --model mlx-community/phi-4-4bit
```

By default this will launch on port `8080`

## Git
Generate a global hook directory for git:
```
mkdir -p ~/.git-hooks
```

Set it as the global hook location:
```
git config --global core.hooksPath ~/.git-hooks
```

Now copy the [prepare-commit-msg](prepare-commit-msg) to `~/.git-hooks/prepare-commit-msg`

# Usage
Make your changes.
Add all your files like:
```
git add .
```

Then simply run:
```
git commit
```

And each file will be sent to the local server and built an overall commit message.