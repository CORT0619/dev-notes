- lets users know the level of effort to update to the latest version
projects start at 1.0.0

starts at 0 it means a package isn't stable for the initial release

### As a publisher of a package:
patch release:
- change that won't break anything
- doesn't add new features
- minor bug fix 
- increment the last number

minor release:
- add a new feature
- doesn't break anything
- increment the middle number

major release:
- a new change that can break functionality
- is not backward compatible

### As a user of a package:
- specify what kinds of updates you want to accept

- patch updates only and no changes to the API should be includes in the updates: -- 1.0.x (having an x in the place of a patch number)
-- ~1.0.4 nor a tilde in front of the exact number

- download new features but nothing that's backwards incompatible:
-- 1
-- 1.x
-- ^1.0.4 having a carrot or hat in front of the exact version

