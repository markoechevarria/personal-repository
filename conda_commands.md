conda --version             -> show conda version
conda update conda          -> update conda
conda update anaconda       -> update anaconda (all packages in base environment)
conda clean --all           -> free space in cache

conda env list                                                                  -> list all environments
conda create --name <new_environment_name>                                      -> create new environment
conda activate <environment_name>                                               -> activate environment
conda desactivate                                                               -> desactivate environment
conda create --name <new_environment_name> --clone <exist_environment_name>     -> clone an environment
conda remove --name <environment_name> --all                                    -> delete an environment

conda list                                                  -> list all package included in the environment
conda search <package_name>                                 -> search a available package 
conda install <package_name_1> <package_name_2> ...         -> install a package
conda update <package_name>                                 -> update a package
conda remove <package_name>                                 -> remove a package
pip install <package_name>                                  -> install using pip

conda env export > environment.yml                          -> export an environment
conda env create -f environment.yml                         -> create an environment from a yml file
