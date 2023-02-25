# qz-zwift-merge
Merge Zwift FIT file with QZ Fitness FIT file to add Zwift location data to QZ Fitness

Zmerge is used to resolve a problem - Zwift FIT files calculate elevation/altitude incorrectly for treadmill incline. Specifically, negative incline is assigned 0 elevation. QZ FIT files, when synced to Zwift activities, don’t contain Zwift's location data (virtual lat/long), but they do contain correct calculated elevation. Zmerge will merge Zwift FIT location data (and any other important data fields) with QZ FIT data including calculated elevation.

Zmerge is a Java command-line app. 
- Requires Garmin FIT SDK.
- Requires Oracle Java™ Runtime Environment 8 - 1.8.0 or higher.
- To compile: javac GarminZwiftMerge/*.java
- To run: java GarminZwiftMerge/GarminZwiftMerge -g qz.fit -z zwift.fit

Can be run as API or standalone from command line.

Call "java -jar garmin-zwift-merge.jar --help" for command line usage.

Javadoc in ./dist folder

Impacted routines:

- GZMGarminListener.java - public void onMesg(Mesg mesg) { 
  - Ignore records that don't match a Zwift timestamp - only timestamp matching records are merged
  - Update the selected Garmin fields in tables - record, lap, session - altitude, distance, latitude, longitude, speed - just update latitude and longitude in record table
  - Check for manufacturer match to Garmin (file_id table) - skip
  
Outstanding issues:

- Should we merge the selected fields from these Zwift tables into QZ FIT file?
  - Record (distance, speed)
  - Lap (distance, speed, time, virtual)
  - Session (speed, distance, time, virtual)


