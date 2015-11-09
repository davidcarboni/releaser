
Releaser
--------


### What is this?

It's a minimal a reference example for setting up your project to deploy to Maven Central.

This project is based on these instructions: http://datumedge.blogspot.co.uk/2012/05/publishing-from-github-to-maven-central.html


### How do I use it?

There are two files of interest in this project:
 * `pom.xml` - a POM file that meets Maven Central requirements and defines a deployment configuration
 * `settings.xml` - a Maven user settings file that defines release deployment configuration

These are set up initially for you to test with a local Nexus instance, but also contain the Sonatype OSS repository information, commented out.

You'll also need to follow the instructions for setting up a Sonatype Jira account and creating a ticket here: http://central.sonatype.org/pages/ossrh-guide.html#create-a-ticket-with-sonatype


### GPG key generation

Here's a terse summary of the GPG commands you'll need to generate and publish a key for signing your artifacts. For the full version, see https://docs.sonatype.org/display/Repository/How+To+Generate+PGP+Signatures+With+Maven

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
 * if you do practice releases, note that the tags created by the release plugin will get pushed to your remote so you'll need to delete them after practice runs. Deleting remote tags isn't obvious so here's a post that explains how: [http://nathanhoad.net/how-to-delete-a-remote-git-tag](http://nathanhoad.net/how-to-delete-a-remote-git-tag). 


The summary is:
 
     git tag -d 12345
     git push origin :refs/tags/12345 
     

### Maven release process
 
Ensure your artifact version is a -SNAPSHOT, then run the following:
 
     mvn release:clean release:prepare
     mvn release:perform

For more options, including rolling back a release or cleaning up a failed release, see: http://maven.apache.org/maven-release/maven-release-plugin/

If you find that the release is deploying a SNAPSHOT version instead of the release artifact, it may be because the release process has changed since I first uploaded this project to Github. I've updated these instructions to match, so just check your release plugin configuration matches the example in this project.


### Next steps

Once you're set up with Sonatype, have deployed your artifacts and commented on your Jira ticket, you'll need to follow these instructions in order to complete the process:

http://central.sonatype.org/pages/ossrh-guide.html

Here are the specific Maven instructions, including the `nexus-staging-maven-plugin` setup:

http://central.sonatype.org/pages/apache-maven.html


Good luck!

David Carboni

[https://github.com/davidcarboni/](https://github.com/davidcarboni/)
