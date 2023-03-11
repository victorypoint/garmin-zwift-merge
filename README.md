# qz-zwift-merge
Merge Zwift FIT file with QZ Fitness FIT file to add Zwift location data to QZ Fitness

Zmerge is used to resolve a problem - Zwift FIT files calculate elevation/altitude incorrectly for treadmill incline. Specifically, negative incline is assigned 0 elevation. QZ FIT files, when synced to Zwift activities, don’t contain Zwift's location data (virtual lat/long), but they do contain correct calculated elevation. Zmerge will merge Zwift FIT location data (and other important data fields) with QZ FIT data including calculated elevation.

Zmerge is a Java command-line app. 
- Requires Garmin FIT SDK.
- Requires Oracle Java™ Runtime Environment 8 - 1.8.0 or higher.

Can be run as API or standalone from command line.

Usage:

- qz-zwift-merge.jar -g qz_file -z zwift_file [-o output_file] [-f]
   - -g qz_file           The QZ Fitness FIT file
   - -z zwift_file        The Zwift FIT file
   - -o output_file       Specify the output file name.
                         Defaults to the name of the first Zwift file with .merged.fit

   -f                   Allows overwrite of existing zwift/output file.
                        Does not allow overwrite of Garmin file.
                        Can be combined with output_file switch eg. -of

   - Note that paths must be quoted if they contain spaces.
   - e.g "c:\dir name\valid_path.fit" c:\dir name\invalid path.fit

Call "java -jar qz-zwift-merge.jar --help" for command line usage.
