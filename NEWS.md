# Changes

## 2.9


Support environment variables in repository credentials ([#248](https://github.com/holgerbrandl/kscript/issues/159))
* Make INCLUDE directive files relative to script dir
* Create a default Run Configuration for Idea ([#244](https://github.com/holgerbrandl/kscript/issues/159))

Minor enhancements & fixes:
* Support whitespace around maven repo credentials (fixes [#228](https://github.com/holgerbrandl/kscript/issues/159))
* Make INCLUDE directive files relative to script dir
* Fixed support for gitbash
* Fixed bootstrap header ([#234](https://github.com/holgerbrandl/kscript/issues/159))
* Improved and documented basic testing support ([#247](https://github.com/holgerbrandl/kscript/issues/159))


## 2.8

Improvements & Fixes
* [#214](https://github.com/holgerbrandl/kscript/pull/214) Added credentials support for `@file:MavenRepository` annotation (thanks to [@meonlol](https://github.com/meonlol)
 for providing the PR and his patience)


## 2.7

Improvements & Fixes
* [#159](https://github.com/holgerbrandl/kscript/issues/159) Use aether instead of maven to pull dependencies
* [#210](https://github.com/holgerbrandl/kscript/issues/210): Updated gradle capsule plugin
* [#102](https://github.com/holgerbrandl/kscript/issues/102): Removed `--self-update`
* Use resource from repo for resolve boostrap header
* [#203](https://github.com/holgerbrandl/kscript/issues/203): Fix cache check bug on Windows
* [#199](https://github.com/holgerbrandl/kscript/issues/199): Allow to bootstrap kscript installation with `--add-bootstrap-header`
* [#200](https://github.com/holgerbrandl/kscript/issues/200): Expose script file name to script


## v2.6


Major Improvements

* [#166](https://github.com/holgerbrandl/kscript/issues/166): Support dynamic versions ending with `+`
* [#185](https://github.com/holgerbrandl/kscript/issues/185): Support "~" in INCLUDE ()
* [#187](https://github.com/holgerbrandl/kscript/issues/187): Added support for shortened URLs
* [#146](https://github.com/holgerbrandl/kscript/issues/146): Allow kscript cache directory to be configurable via `KSCRIPT_CACHE_DIR` environment variable
* [#175](https://github.com/holgerbrandl/kscript/issues/175): `cygwin` support improvements
* Improved `kshell` launcher to also launch scripts with invalid code

Notable Bug Fixes
* Confusing error when filename starts with a number
* Fixed usage `@file:CompilerOpts` in combination with `@file:Include`
* Renamed `kshell_from_kscript` to `kshell_kts`

## v2.5

Major Improvements

* Support dependencies with different types (pom instead of jar)
* Use current kotlin for temporary project when using `--idea`
* Started [kshell launcher](https://github.com/holgerbrandl/kscript/tree/master/misc/kshell_launcher) for kscriptlets
* Support `--idea` with includes

Minor Enhancements

* Avoid dependency duplications when using `//INCLUDE` recursively
* Fixed: Unable to run script with plus character in filename
* Allow to include same file from multiple files
* Fixed: Space-containing argument propagation


## v2.4

Major Enhancements:
* Allow to set `kotlinc` compiler flags with `@file:CompilerOpts` or `//COMPILER_OPTS` (#84). See [here](https://github.com/holgerbrandl/kscript#deploy-scripts-as-standalone-binaries).
* Provide a way to _package_ kscripts (#63). See [here](https://github.com/holgerbrandl/kscript#configure-the-runtime--with-kotlin_opts).

Minor Enhancements:

* Fixed #95: `//INCLUDE` requiring full path
* Fixed #94: stdin does not allow further switches
* Allow for round brackets in artifact ids (fixes #100).
* Fixed #83: interactive fails unless your script contains dependencies
* Fixed #82: Sym-linking does not work correctly with --idea and relative script paths
* New: Implemented benchmarking suite to assess runtime impact of `kscript`
* Fixed: Don't use null in classpath arguments if classpath is empty
* Fixed: Use `exec` for derived interpreter
* Simplify Gradle config for script bootstrapping with IDEA (#86)
* Added Gradle wrapper to the project (#87 and #88)


## v2.3


Major Enhancements:

* Replaced `javac` with `kotlinc` for faster script compilation
* Added symlink support
* Allow to derive [custom DSL interpreters](https://github.com/holgerbrandl/kscript/blob/master/docs/user_guide.md#create-interpreters-for-custom-dsls) from kscript (fixes  [#67](https://github.com/holgerbrandl/kscript/issues/67))
* Implemented `@file:Include` and `@EntryPoint` as [documented](https://github.com/holgerbrandl/kscript#annotation-driven-script-configuration) in README (fixes [#73](https://github.com/holgerbrandl/kscript/issues/73))
* Added [gitter](https://gitter.im/holgerbrandl/kscript?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge) channel

Minor Enhancements:
* Consolidate imports and dependencies when `//INCLUDE` is used (fixes [#75](https://github.com/holgerbrandl/kscript/pull/75)) …
* Support artifact should have better namespace (fixes [#57](https://github.com/holgerbrandl/kscript/issues/57))
* Fixed [#76](https://github.com/holgerbrandl/kscript/issues/76): Unspecific error when dependency resolution fails
* Fixed [#66](https://github.com/holgerbrandl/kscript/issues/66): It should die more gracefully if `idea` is not present
* Fixed [#81](https://github.com/holgerbrandl/kscript/issues/81): Allow package declarations for scripts
* Fixed [#78](https://github.com/holgerbrandl/kscript/issues/78): When using `--idea` the script argument should be symlinked
* Fixed [#79](https://github.com/holgerbrandl/kscript/pull/79): Provide setup instructions if idea launcher is missing
* Simplified build instructions (fixes [#60](https://github.com/holgerbrandl/kscript/issues/60))
* Document dependencies of kscript (fixes [#69](https://github.com/holgerbrandl/kscript/issues/69))


## v2.2

* Logging of maven artifact downloads to stderr (fixes [#23](https://github.com/holgerbrandl/kscript/issues/23))
* Added `-s` / `--silent` to suppress all logging
* Fixed [#55](https://github.com/holgerbrandl/kscript/issues/55): dependency resolution fails on travis ci and within docker containers
* Added alternative `@DependsOnMaven(val artifactId: String)` annotaiton to declare dependencies. This has been implemented to make kscripts compatible with https://github.com/ligee/kotlin-jupyter
* Added support for custom maven repositories (fixes [#22](https://github.com/holgerbrandl/kscript/issues/22))


See [README.md](README.md) for usage details.


## v2.1

* support for annotation-driven script configuration
* refactored support api mode into `-t` parameter

## v2.0

* Reimplemented in kotlin (fixes [#36](https://github.com/holgerbrandl/kscript/issues/36))
* Added cygwin support (fixes [#39](https://github.com/holgerbrandl/kscript/issues/39))
* Added `//INCLUDE` directive (fixes [#34](https://github.com/holgerbrandl/kscript/issues/34)
* Fixed: interactive mode is not correctly started when using stdin as script argument ([#40](https://github.com/holgerbrandl/kscript/issues/40)
* Fixed compatibility with java9 ([#41](https://github.com/holgerbrandl/kscript/issues/41))


## v1.5.1

* Fixed `--self-update`
* More robust self-update on OSses with file-locking (e.g. windows)



## v1.5

* removed `curl` dependency
* more streamlined dependency lookup


## v1.4

Major new features
* Redesigned [support library](https://github.com/holgerbrandl/kscript-support-api) for streamlined tabular data processing. See [here](http://holgerbrandl.github.io/kotlin/2017/05/08/kscript_as_awk_substitute.html) for an overview.


## v1.3

Major new features

* Dramatically reduced overhead by using dependency lookup cache more efficiently. After the initial scriptlet-jar-building, `kscript` runs with almost **zero overhead** now (fixes  [#4](https://github.com/holgerbrandl/kscript/issues/4))
* Dependencies can now declared in multiple lines for better readability (fixes [#2](https://github.com/holgerbrandl/kscript/issues/2))
* Automatic inclusion of support library for one-liners (fixes [#19](https://github.com/holgerbrandl/kscript/issues/19))
* Direct script arguments `kscript 'println("hello kotlin")'` (fixes [#18](https://github.com/holgerbrandl/kscript/issues/18))
* More robust dependency resolution with more informative error messages


Support API improvements
* Kotlin DocOpt helpers to build CLIs ([example](https://github.com/holgerbrandl/kscript-support-api/blob/master/src/test/kotlin/kscript/test/DocOptTest.kt))
* New [utilities](https://github.com/holgerbrandl/kscript-support-api/blob/master/src/main/kotlin/kscript/StreamUtil.kt) to automatically resolve arguments files and stdin to `Sequence<String` for by-line processing

Other changes
* Allow dependencies to be declared in multiple lines prefixed by `//DEPS` (fixes [#2](https://github.com/holgerbrandl/kscript/issues/2))
* To ensure long-term stability of `kscript` we've added a suite of [unit tests](test/TestsReadme.md). The repository tested continuously by [Travis CI](https://travis-ci.org/holgerbrandl/kscript)
* Cache directory is now `~/.kscript`
* More heuristics to guess `KOTLIN_HOME`
* Cache cleanup `--clear-cache` now applies to jars, scripts, urls, and cached dependency lookups


## v1.2 

* Fixed compatibility with [Kotlin v1.1](https://kotlinlang.org/docs/reference/whatsnew11.html)
 (fixes [#15](https://github.com/holgerbrandl/kscript/issues/15))
* Added `-i` to dump interactive console command incl deps (fixes [#10](https://github.com/holgerbrandl/kscript/issues/10))
* Compile jars should go to TEMP (fixes [#13](https://github.com/holgerbrandl/kscript/issues/13))
* started test-suite 

## v1.1

* Support for stdin and process substitution as script source. See [examples](examples)
* versioning and auto-update
* basic command-line help
* Added support for `KOTLIN_OPTS` (see [#8](https://github.com/holgerbrandl/kscript/issues/8))
* Added CLI help to `resdeps.kts`
* Added option to clear dependency lookup cache: `resdeps.kts --clear-cache`

## v1.0

Initial Release