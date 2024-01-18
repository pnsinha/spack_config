
# spack_yaml_config
Track local customizations of spack yaml files for various systems.  ( symbolic links from its $SPACK_ROOT/etc/spack/\*.yaml )

## usage with $SPACK_ROOT
Make symbolic links pointing to an external copy of this directory tree which lives outside of $SPACK_ROOT.  
```
[pnsinha@ssd03 spack]$ cp -s /software/sw/spack-mw3/spack_yaml_config/mw3/* ./
[pnsinha@ssd03 spack]$ ll -a
total 4
drwxrwsr-x 3 pnsinha rcc-software 4096 Oct 30 04:21 .
drwxrwsr-x 3 pnsinha rcc-software 4096 Oct 30 03:44 ..
lrwxrwxrwx 1 pnsinha rcc-software   59 Oct 30 04:21 compilers.yaml -> /software/sw/spack-mw3/spack_yaml_config/mw3/compilers.yaml
lrwxrwxrwx 1 pnsinha rcc-software   56 Oct 30 04:21 config.yaml -> /software/sw/spack-mw3/spack_yaml_config/mw3/config.yaml
drwxrwsr-x 6 pnsinha rcc-software 4096 Oct 30 03:44 defaults
lrwxrwxrwx 1 pnsinha rcc-software   57 Oct 30 04:21 modules.yaml -> /software/sw/spack-mw3/spack_yaml_config/mw3/modules.yaml
lrwxrwxrwx 1 pnsinha rcc-software   55 Oct 30 04:21 repos.yaml -> /software/sw/spack-mw3/spack_yaml_config/mw3/repos.yaml#
```
Then track the files here with this repo.


## Configuration Scopes
Once Spack has been installed, its configuration will be stored into different directories for different scopes. Spack pulls configuration data from files in several directories. Spack searches for configuration parameters in higher-precedence scopes first. Therefore, settings in a higher-precedence file can override those with the same key in a lower-precedence one. Three different scopes are important for this documentation. The scopes are shown from lowest to highest precedences:



### Default Scope
The configuration of this scope is stored in $SPACK_ROOT/etc/spack/defaults. You should generally not modify the settings of this scope. Instead, you should override them in other configuration scopes.

### User Scope
The configuration of this scope is stored in ~/.spack. The settings of this scope affect all instances of Spack. In other words, configurations apply to any loaded/sourced Spack installation. By default, spack compiler and spack repo commands update the configurations of this directory. For example, when you add a new compiler using spack compiler add command, this will modify the compilers.py stored in ~/.spack/linux. You need to move the compiler.

Many cache files are stored in this directory. Those files may cause an error when switching between different Spack installations. To avoid such error you need to remove the cache files using spack clean as follows:

spack clean --all

This command removes:

All temporary build stages.

Cached downloads.

All install failure tracking markers.

Long-lived caches, like the virtual package index.

.pyc, .pyo files.

Software needed to bootstrap Spack.

### Site Scope
The configurations of this scope is stored in $SPACK_ROOT/etc/spack. The settings of this scope affect only this instance of Spack. Spack’s default configuration settings reside in $SPACK_ROOT/etc/spack/defaults. These are useful for reference, but should never be directly edited. To override these settings, create new configuration files or copy the ones in the default scope in another location, i.e in the site scope, and change it there.

Spack provides three environment variables to allow users to override or opt out of configuration locations:

SPACK_USER_CONFIG_PATH: it overrides the path to use for the user (~/.spack) scope.

SPACK_SYSTEM_CONFIG_PATH: it overrides the path to use for the system (/etc/spack) scope.

SPACK_DISABLE_LOCAL_CONFIG: setting this variable to true disables both the system and user configuration directories. Spack will only consider its own defaults and site configuration locations.

S`PACK_USER_CACHE_PATH: it overrides the default path to use for user data (misc_cache, tests, reports, etc.).

To disable both the system and user configuration directories, you type:

export SPACK_DISABLE_LOCAL_CONFIG=true

Spack will only consider its own site configuration scope because it has higher precedence than the default scope. Also, you make sure now that any update on the settings will affect the settings of the site scope $SPACK_ROOT/etc/spack