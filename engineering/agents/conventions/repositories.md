# Repository Conventions

Read this document when creating, restructuring, configuring or reviewing a Git repository and its root layout.

Repositories are primarily for system maintainability while reducing risk. 
Committing often takes care of the risk, however the maintainability depends
on a purposeful structure. 
  

## Sparse Root 

In alignment with long term maintainability over short term development ease,
repos are organised to **NOT** put source code at the root, and instead, only have 
default `.git` manage files, and a single `readme.md` pointing to further material 
in sub folders:

- `.git`			#
- `.gitignore`		#
- `.gitmodules` 	# optional - see below under *Nested Sub Repositories*
- `readme.md` 		# only md file in the root, pointing to further documentation elsewhere (see below),


## Root Folders

In alignment with long term maintainability over short term development ease,
repos are organised to not put source code at the root, and instead, each repo 
follows a structure similar to:
- `DOCUMENTATION/` 	# folder to describe aspects of the design and implementaiton.
- `SOURCE/` 		# folder for source code
- `_TMP/` 			# an optional location for one off scripts, etc.


## Nested Sub Repositories

In alignment with long term maintainability over short term development ease,
most projects benefit from being developed in discrete modules - per system and 
per Logical Deployment Module (LDM) within.

It is therefore common for a Repo to have a `.gitmodules` folder which imports other repositories.

### Issues to knowabout.
The use of the same folder structure in each repo, combined with the use of sub modules leads to a subtle issue. Essentially, an LLM can lose its bearing as to which SOURCE folder it is working within (because they all are called SOURCE...), therefore does not find the root `_TMP` folder and either creates a new one in a sub repo, or worse just puts the code at the roof sub repos. 

Outcomes are that the LLM will develop test scripts in folders all over the place,
and overall documentation in a subfolder, etc.

To help LLMs orient themselves a `.root` folder is developed in the root repo ***and no other/nested repos***.


## Example Repository Structure 

An example of a system that has a service backend consumed by a front end spa, might have an overall folder structure similar to the following:

```text
/							# project root repo's base folder
  .submodules				# file referring to sub modules (CLIENT & SERVICE)
  .root/					# root repo marker 
  _TMP/						# folder for temp LLM developed one-time scripts
  DOCUMENTATION/			# documentation for different stakeholders
  SOURCE/   				# location of the solution, referring to SERVICE/ and CLIENT/.
    Platform.sln
  CLIENT/   				# sub repo for Angular client
    SOURCE/ 				# source code for Angular client project
	  App.Service.Client.Web# client project folder (with an .esproj in it)
  SERVICE/  				# sub repo for Service
    SOURCE/ 				# source code for Service project (App.Host)
    SUBMODULES/ 			# additional sub repos for Service LDMs. 
	  App.Modules.Sys		# the foundational Logical Deployment Module (LDM)
	    SOURCE/				# the source code
	  App.Modules.Resources	# another LMD
	    SOURCE/				# it's source code
	  App.Modules.Social    # another LDM
	    SOURCE/				# it's source code
      ...						# and so on (about 30 LDMs overall)
```


## Repository Documentation

See the [documentation conventions](./documentation.md) for expectations and guidelines.


## Maintenance

Due to the LLM putting execution scripts in the wrong location, cleanup is regularly needed.
If you encounter loose files and folders in the root of a repo that looks like it was incorrectly placed
there (rather than the root `_TMP/`, and you are able to ascertain they are no longer used (one off),
move them to the `_TMP/` folder.


