# Contributing

## TL;DR

* Fork the project from https://github.com/pivotal/LicenseFinder
* Create a feature branch.
* Make your feature addition or bug fix. Please make sure there is appropriate test coverage.
* Rebase on top of master.
* Send a pull request.


## Adding Package Managers

There are a few steps to adding a new package manager.
[Here](https://github.com/pivotal/LicenseFinder/compare/v2.0.0...v2.0.1) is how
support was added for `rebar`, an `erlang` package manager.


## Adding Licenses

Add new licenses to `lib/license_finder/license/definitions.rb`.  There are
existing tools for matching licenses; see, for example, the MIT license, which
can be detected in many different ways.


## Adding Reports

If you need `license_finder` to output additional package data, consider
submitting a pull request which adds new columns to
`lib/license_finder/reports/csv_report.rb`.

It is also possible to generate a custom report from an ERB template.  Use this
[example](https://gist.github.com/mainej/b190d2f138c2b9e2e20a) as a starting
point.  These reports will have access to the helpers in
[`LicenseFinder::ErbReport`](https://github.com/pivotal/LicenseFinder/blob/master/lib/license_finder/reports/erb_report.rb).

If you need a report with more detailed data or in a different format, we
recommend writing a custom ruby script.  This
[example](https://gist.github.com/mainej/48ac616844505d50f510) will get you
started.

If you come up with something useful, consider posting it to the Google Group
[license-finder@googlegroups.com](license-finder@googlegroups.com).


## Development Dependencies
To successfully run the test suite, you will need the following installed: 
- NPM (requires Node)
- Bower (requires Node and NPM)
- Maven (requires Java)
- Gradle (requires Java)
- Pip (requires python)
- Rebar (requires erlang)
- GoDep, GoWorkspace, and GoVendor (requires golang)
- CocoaPods (requires ruby)
- Bundler (requires ruby)

If you run `rake check_dependencies`, you'll see exactly which package managers
you're missing.

### Python

For the python dependency tests you will want to have virtualenv
installed, to allow pip to work without sudo. For more details, see
this [post on virtualenv][].

  [post on virtualenv]: http://hackercodex.com/guide/python-development-environment-on-mac-osx/#virtualenv

You'll need a pip version >= 6.0.

### JRuby

If you're running the test suite with jruby, you're probably going to
want to set up some environment variables:

```
JAVA_OPTS='-client -XX:+TieredCompilation -XX:TieredStopAtLevel=1' JRUBY_OPTS='-J-Djruby.launch.inproc=true'
```

### Gradle

You'll need a gradle version >= 1.8.

### CocoaPods
LicenseFinder supports CocoaPods 0.39 and below. If you are using a later version of CocoaPods, you will need to downgrade CocoaPods/Specs repository in order to use LicenseFinder. [This article](http://blog.cocoapods.org/Sharding/) describes the breaking change between CocoaPods 0.39 and 1.0. You will need to use an older, archived CocoaPods/Specs repo. 

If you see the following error, try switching to the archived repo. 

```bash
[!] The `master` repo requires CocoaPods 1.0.0 -  (currently using 0.34.0)
 ```

Example of how to switch to the archived repo: 

```bash 
mv ~/.cocoapods/repos/master ~/.cocoapods/repos/master.bak
git clone https://github.com/CocoaPods/Old-Specs.git ~/.cocoapods/repos/master
```
