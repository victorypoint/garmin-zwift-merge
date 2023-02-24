# qz-zwift-merge
Merge Zwift FIT file with QZ Fitness FIT file to add Zwift location data to QZ Fitness

Zmerge is used to resolve a problem - Zwift FIT files calculate elevation/altitude incorrectly for treadmill incline. Specifically, negative incline is assigned 0 elevation. QZ FIT files, when synced to Zwift activities, don’t contain Zwift's location data (virtual lat/long), but they do contain correct calculated elevation. Zmerge will merge Zwifts FIT location data (and any other important data fields) with QZs FIT data including calculated elevation.

Can be run as API or standalone from command line.

Call "java -jar garmin-zwift-merge.jar --help" for command line usage.

Javadoc in ./dist folder
