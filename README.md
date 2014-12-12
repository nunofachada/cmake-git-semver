### Summary

This [CMake](http://www.cmake.org/) module sets the project version and
partial version variables by analysing the git tag and commit history. 
It expects git tags defined with [semantic versioning 2.0.0](http://semver.org/).

### Usage

The module expects the `PROJECT_NAME` variable to be set, and recognizes
the `GIT_FOUND`, `GIT_EXECUTABLE` and `VERSION_UPDATE_FROM_GIT` 
variables.

If Git is found and `VERSION_UPDATE_FROM_GIT` is set to boolean TRUE, 
the project version will be updated using information fetched from the
most recent git tag and commit. Otherwise, the module will try to read
a `VERSION` file containing the full and partial versions. The module 
will update this file each time the project version is updated from git.

Once done, this module will define the following variables:

 * `${PROJECT_NAME}_VERSION_STRING` - Version string without metadata
such as "v2.0.0" or "v1.2.41-beta.1". This should correspond to the
most recent git tag.
 * `${PROJECT_NAME}_VERSION_STRING_FULL` - Version string with metadata
such as "v2.0.0+3.a23fbc" or "v1.3.1-alpha.2+4.9c4fd1"
 * `${PROJECT_NAME}_VERSION` - Same as `${PROJECT_NAME}_VERSION_STRING`, without the preceding 
'v', e.g. "2.0.0" or "1.2.41-beta.1"
 * `${PROJECT_NAME}_VERSION_MAJOR` - Major version integer (e.g. 2 in v2.3.1-RC.2+21.ef12c8)
 * `${PROJECT_NAME}_VERSION_MINOR` - Minor version integer (e.g. 3 in v2.3.1-RC.2+21.ef12c8)
 * `${PROJECT_NAME}_VERSION_PATCH` - Patch version integer (e.g. 1 in v2.3.1-RC.2+21.ef12c8)
 * `${PROJECT_NAME}_VERSION_TWEAK` - Tweak version string (e.g. "RC.2" in v2.3.1-RC.2+21.ef12c8)
 * `${PROJECT_NAME}_VERSION_AHEAD` - How many commits ahead of last tag (e.g. 21 in v2.3.1-RC.2+21.ef12c8)
 * `${PROJECT_NAME}_VERSION_GIT_SHA` - The git sha1 of the most recent commit (e.g. the "ef12c8" in v2.3.1-RC.2+21.ef12c8)

### License

This module is public domain.

