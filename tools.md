---
Created at: Tuesday 06-10-2026 – 19:56
Modified at: Thursday 08-10-2026 – 16:11
---
# Installing tools

## Intended process


0. Check conda set up
    - Intialization block in `.zshrc`
    - Auto activation of base off
1. Create conda environment for conda-global install
2. Install gcp cli as test
3. Deactivate env
4. Try to access gcloud from new shell

>[!resources]- **[[conda-cheatsheet.pdf|Conda cheatsheet]]**
>[current version](https://docs.conda.io/projects/conda/en/latest/user-guide/cheatsheet.html)
### 0. Check conda set up

After installing miniconda, `conda init` or `conda init zsh` should run automatically.

Check `.zshrc` contains the conda setup block which looks something like this

```zsh
# >>> conda initialize >>>
# !! Contents within this block are managed by 'conda init' !!
__conda_setup="$('/opt/miniconda3/bin/conda' 'shell.zsh' 'hook' 2> /dev/null)"
if [ $? -eq 0 ]; then
    eval "$__conda_setup"
else
    if [ -f "/opt/miniconda3/etc/profile.d/conda.sh" ]; then
        . "/opt/miniconda3/etc/profile.d/conda.sh"
    else
        export PATH="/opt/miniconda3/bin:$PATH"
    fi
fi
unset __conda_setup
# <<< conda initialize <<<
```

If not, run `conda init zsh` (or ``)
