## Clear Package Cache

`sudo pacman -Sc` : Delete obsolete packages versions (of not instaled). Allow degrade packages.

`sudo pacman -Scc` : Delete all cache's files, also installed packages versions. Don't allow degrade packages.

## Delate Orphan Packages

`pacman -Qtdq` : list orphan packages

`sudo pacman -Rns $(pacman -Qtdq)` : delete orphan packages recursively

## Yay

`yay -Sc` : clear pacman cache and the package pacman 
