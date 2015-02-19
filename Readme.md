Repository of common build elements for public ECS projects
===

Published projects
---

### build.gradle

Your project's build.gradle file should look like this:

    description 'Description of this project'
    version '1.0.0'// omit the version to enable automated semantic versioning based on tags

    // if your github project is different than your origin project
    ext.githubProjectName = 'my-project-java'

    // if your license is different than the default (BSD 3-Clause)
    ext.licenseName = 'My License Name'
    ext.licenseUrl = 'http://opensource.org/licenses/My-License'

    buildscript {
        // set the version of the common build script you will use
        ext.commonBuildVersion = '1.1'
        ext.commonBuildDir = "https://raw.githubusercontent.com/emcvipr/ecs-common-build/v$commonBuildVersion"
        apply from: "$commonBuildDir/ecs-publish.buildscript.gradle", to: buildscript
    }

    apply from: "$commonBuildDir/ecs-publish.gradle"

    // replace below with your project's actual dependencies
    dependencies {
        compile 'com.emc.ecs:smart-client:1.0.0',
                'com.emc.vipr:vipr-object-transformations:2.0.3',
                'org.jdom:jdom2:2.0.5'
        testCompile 'junit:junit:4.11'
    }

### $HOME/.gradle/gradle.properties

You should also have a user-level gradle.properties file that contains the following properties:

    # path to Java 6 jre/lib (if installed)
    java6Lib=
    
    # set these if you plan on publishing. note: you will be prompted for passwords if necessary
    sonatypeUsername=
    githubUsername=
    gitUsername=
    # Located on the signing server. KeyId can be found using gpg --list-keys
    signingKeyId=
    signingSecretKeyRingFile=

