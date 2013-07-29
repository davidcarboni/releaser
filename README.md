
Releaser
--------


### What is this?

It's a minimal a reference example for setting up your project for deployment to Maven Central.

This project is based on these instructions: http://datumedge.blogspot.co.uk/2012/05/publishing-from-github-to-maven-central.html


### How do I use it?

There are two files of interest in this project:
 * pom.xml - a POM file that meets Maven Central requirements and defines a deployment configuration
 * settings.xml - a Maven user settings file that defines release deployment configuration

These are set up initially for you to test with a local Nexus instance, but also contain the Sonatype OSS repository information, commented out.

You'll also need to follow the instructions for setting up a Sonatype Jira account and creating a ticket here: https://issues.sonatype.org/


### GPG key generation

Here's a terse summary of the GPG commands you'll need to generate and publish a key for signing your artifacts. For the full version, see https://docs.sonatype.org/display/Repository/How+To+Generate+PGP+Signatures+With+Maven:

    # is GPG installed?
    gpg --version 
    
    # Generate a key. If in doubt, accept defaluts. I'd recommend a 3072-bit key:
    gpg --gen-key
    
    # Check what was generated:
    gpg --list-keys
    gpg --list-secret-keys
    # You should see:
    # pub nnnnA/FFFFFFFF YY-MM-DD
    # ... etc ...
    # make a note of FFFFFFFF - this is your key ID
    
    # Check for sub keys:
    gpg --edit-key FFFFFFFF
    # If any "sub" key says "usage: S", refer to the URL above for instructions on deleting it.
    
    # Publish key:
    gpg --keyserver hkp://pool.sks-keyservers.net --send-keys FFFFFFFF


### Test with a local Nexus

Try running with a local Nexus instance to get the hang of it:
 * download from [http://www.sonatype.org/downloads/nexus-latest-bundle.tar.gz](http://www.sonatype.org/downloads/nexus-latest-bundle.tar.gz "Sonatype download")
 * unpack
 * cd into `bin/`
 * run `./nexus`
 * `tail ../logs/wrapper.log`
 * open [http://localhost:8081/nexus/](http://localhost:8081/nexus/ "If you have Nexus installed and running locally this link will work for you")
 * the default Nexus deployment username and password are already set in the example Maven `settings.xml` in the root of this project.


### Maven release process
 
 Ensure your artifact version is a -SNAPSHOT, then run the following:
 
     mvn clean release:prepare
     mvn release:perform

For more options, including rolling back a release or cleaning up a failed release, see: http://maven.apache.org/maven-release/maven-release-plugin/

Good luck!

David Carboni
https://github.com/davidcarboni/
