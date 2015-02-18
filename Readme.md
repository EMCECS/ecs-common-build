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
    
    buildscript {
        apply from: "ecs-publish.buildscript.gradle", to: buildscript
    }
    
    apply from: 'ecs-publish.gradle'
    
    // replace below with your project's actual dependencies
    dependencies {
        compile 'com.emc.ecs:smart-client:1.0.0',
                'com.emc.vipr:vipr-object-transformations:2.0.3',
                'org.jdom:jdom2:2.0.5'
        testCompile 'junit:junit:4.11'
    }

### $HOME/.gradle/gradle.properties

You should also have a user-level gradle.properties file that contains the following properties:

    # path to Java 6 rt.jar (if installed)
    java6Classpath=
    
    # set these if you plan on publishing. note: you will be prompted for passwords if necessary
    sonatypeUsername=
    githubUsername=
    gitUsername=
    # Located on the signing server. KeyId can be found using gpg --list-keys
    signingKeyId=
    signingSecretKeyRingFile=

