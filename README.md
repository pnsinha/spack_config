
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
