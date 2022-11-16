# Git

###### Activar que se fiormen todos los commits
```console
git config --global commit.gpgsign true
```

###### Firmar un commit determinado (-S)
```console
git commit -S -m "YOUR_COMMIT_MESSAGE"
```

###### Eliminar uun submodulo

* Delete the relevant section from the .gitmodules file.
* Stage the .gitmodules changes git add .gitmodules
* Delete the relevant section from .git/config.
* Run git rm --cached path_to_submodule (no trailing slash).
* Run rm -rf .git/modules/path_to_submodule (no trailing slash).
* Commit git commit -m "Removed submodule "
* Delete the now untracked submodule files rm -rf path_to_submodule
