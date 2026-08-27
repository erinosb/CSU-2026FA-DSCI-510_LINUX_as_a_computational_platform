# Tarballs

We can compress a directory of files into a single, compressed file using the **tar** command. This greatly reduces the directory size and makes it easy to move a whole directory from computer-to-computer. Sadly, the commands and option for the **tar** command are notoriously hard to memorize:

<p align="center">
<img width="410" alt="tarball" src="https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Images/tar_2x.png">
</p>

To compress a directory into a tarball:
- **tar compression**
- **tar** -zcvf <tarball.tgz> <directory_to_compress>
- -z - gzip it
- -c - compress it
- -v - verbose
- -f - files

To extract a tarball into an un-compressed directory again:
- **tar extraction**
- **tar** -zxvf <tarball.tgz>
- -z - it's gzipped
- -x - eXpand it
- -v - verbose
- -f - files

Back to [Options](../Modules/Week1/1-5_Options.md)
