## Third party JARs for GPSLogger for Android project

Several JARs used by GPSLogger for Android don't have a maven repo anywhere. Github can allow a repository to act as a maven repo.

### Add JARs

Put the jar in the `jars` directory.

Add a corresponding line to the `mvncommands.sh`, such as

    mvn install:install-file -DgroupId=com.mendhak.gpsloggersupportfiles -DartifactId=owncloud-android-library -Dversion=0.0.3 -Dfile=jars/owncloud-android-library.aar -Dpackaging=aar -DgeneratePom=true -DlocalRepositoryPath=./repository  -DcreateChecksum=true

Run `./mvncommands.sh` and it will populate the `repository` directory.

It will also run the Nexus Indexer jar to produce an `.index` directory in the `repository` directory.

Push to github.


### Use JARs

When referencing from a Gradle project, Use


    maven {
        url "https://raw.github.com/mendhak/gpslogger-support-files/master/repository"
    }

Then when you call

    compile 'com.mendhak.gpsloggersupportfiles:dropbox-android-sdk:1.6.3'

It will find it in the repo and use it. 
