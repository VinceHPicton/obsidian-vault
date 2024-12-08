In a nutshell it's basically software which creates an abstraction for users to interact with computer data as a system of files and folders, when in reality the data exists as individual "blocks" with addresses*

\*On a typical hard drive like SSD or HDD

**blocks** are like boxes which store a small amount of information, typically 4096 bytes (4 KiB)

Different OS's have different standard default **directory structures**, for example alpine linux has /bin /usr /var etc, macOS has /Libraries /Applications etc. These are just the **conventions** for a specific OS, but generally the combination of the filesystem software and this directory structure are referred to as, for example, "the linux filesystem"