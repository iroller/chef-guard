Chef-Guard CHANGELOG
====================

0.5.1 (UNRELEASED)
-----
- Fixed an issue with the new clients endpoint
- Updated the github.com/gorilla/mux dependency
- Fixed a bug in the processChange func where a returned error was not properly handled (fixes GH-65)
- Tar files uploaded to the supermarket will no longer contain files that are in the .gitignore or chefignore (fixes GH-56)
- Added checks to verify content has actually changed before commiting anything to Git (fixes GH-64)
- Filtered out the node and client creations so those will be commited if `commitchanges = true` (fixes GH-67 and GH-70)
- Fixed a bug were a change was committed even when the change failed (fixes GH-68)
- Fixed the custom client endpoint so it redirects to the correct path (fixes GH-71)
- Altered the diffing mechanism so it doesn't trigger on the line endings (windows vs unix style endings) (fixes GH-72)

0.5.0
-----
- Fixed an issue where file handles where not always released correctly
- Added a check to verify if cfg.Community.Forks is actually configued before using it
- Refactored the fix for issue #53 as the current fix wasn't effecient and caused 'too many open files' issues
- Added a check to make sure all custom Github endpoints end with a single forward slash
- Added a configuration option to specify a custom sender address used when sending the diffs
- Added an additional (non-Chef) endpoint to download clients from
- Added an additional (non-Chef) endpoint to get the server time from
- Fixed a bug when running the Rubocop tests

0.4.5
-----
- Added the '.json' extention to cookbook auditing files saved in Github to have uniform names
- Fixed issue #53 by making sure the config is checked and used to determine if we want to verify SSL
- Fixed issue #54 by adding a check to verify if a value is actually configued before using it
- Added code to check if the config file contains values for all required fields

0.4.4
-----
- When you try to overwrite a frozen cookbook return a HTTP 409 error instead of a HTTP 412 so Berkshelf doesn't crash on it but just reports it

0.4.3
-----
- Fixed logic error in the getChangeDetails func, where the extention '.json' was sometimes left out and sometimes added twice

0.4.2
-----
- Fixed issue #35 by making sure all data bag items are removed when tha bag itself is removed
- Fixed issue #39 by ignoring any missing files inside the spec folder
- Added the first code needed to support saving Chef metrics in a MongoDB backend (Disney feature request)

0.4.1
-----
- Fixed some issues within the updated validateConstraints logic which in some cases prohibited uploading a community cookbook

0.4.0
-----
- Changed the ValidateChanges option to have mulitple modes instead of only true/false (on/off) (issue #36)
- Changed the validation of contrains to require more specific constrains (= x.x.x)
- Deleted the waiting time for Git API calls as this is not needed anymore since Github Enterprise version 11.10.34x

0.3.3
-----
- Added a configuration option to execute custom foodcritic tests

0.3.2
-----
- Updated the error output to show files related to the cookbook (issue #25)
- Changed the dependecy check so it now outputs all dependency errors at once (issue #26)
- Fixed a bug where Chef-Guard would untag manually tagged Github repo's when uploading to the supermarket failed (issue #29)
- Prevent community cookbooks that are forked from being uploaded to your private Supermarket (issue #30)
- Updated chef-golang dependency

0.3.1
-----
- Fixed typo in error message
- Fixed a regex logic error when parsing cookbook constraints
- Added decoding call for all marshalled JSON content

0.3.0
-----
- Fixed bug in the blacklist logic (issue #6)
- Changed the way the .gitignore and chefignore files are handled (issue #20)
- Altered output of the compare function to always show the full results (issue #20)
