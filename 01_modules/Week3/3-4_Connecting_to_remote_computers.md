# Connecting to Remote Computers 

## Todays objectives: 

<details>
  <summary>Click to expand/collapse</summary>

- **Vocabulary**
  - Array variables
  - Array elements
  - Indexing
  - Special variables
  - Hard Coding
  - String
  - String operation
  - Replacement/substitution
  - Sub-setting strings
  - Sub-strings
  - The environment
  - Environmental variables

- **Things you should know how to do after this class**
- Know what an array variable is and how to assign values to one
  - Understand the basics of array indexing
  - Know how to enter input into a script by passing argument that can be accessed with a special variable
  - Know how to save output from a script using `>` and `>>`
  - Know a little bit about manipulating string variables

- **Commands covered**
  - `arrayvariable=(value1 value2 value3)`
  - `${arrayvariable[*]}`
  - `${arrayvariable[@]}`
  - `${arrayvariable[0]}`
  - `${arrayvariable[1]}`
  - `${arrayvariable[#]}`
  - `${#arrayvariable[@]}`
  - `read`
  - `$0`
  - `$1`
  - `$2`
  - `$#`
  - `$@`
  - `$*`

</details>

## Connecting to remote computers

Up to this point, we have only used the terminal to interact with your **local** computer. Today we will talk about several ways we can use the terminal to interact with **remote** computers over the internet.

In some instances, we will **log into** a remote computer, also known as **connecting** to it. This will allow us to interact with that computer as if we had opened its terminal. With this access, we could navigate that computer's file structure, write new files, run jobs, or transfer files. It would be just like interacting with our local computer.

What types of remote computers can we log into?

```
1. remote personal computers
2. servers or repositories (computing or file storage)
3. supercomputers
```

----

## Accessing remote computers with ssh - Secure SHell

**ssh usage**

```
ssh <addressOfRemoteServer>

ssh [-l <yourloginname>] <addressOfRemoteServer> #that's a lower case “L”
```

:hammer_and_wrench: **Group Exercise:** Try logging into Alpine using **ssh** 

The login address for ALPINE is: `login.rc.colorado.edu`

If your username is `loki@colostate.edu`, and your password is `godofmischief`, you would log in like so:

```
$ssh -l loki@colostate.edu login.rc.colorado.edu
Password: godofmischief,push
# Switch to your DUO app on your phone to approve
```

>[!WARNING]
> That's a lower case "L"**

>[!TIP]
> Replace your eID e-mail with loki@colostate.edu**

>[!TIP]
> You won't see anything pop up when you type your password

>[!TIP]
> If `,push` doesnt work, try `,phone` or the 6-digit code on your DUO app (refreshes every 20 seconds)**

:hammer_and_wrench: **Group Exercise:** Make a file.
- Use nano to create a file called `iwashere.txt`
- Write a little note

-----

## Accessing ALPINE using OnDemand

The team at CU Boulder who developed ALPINE have helped to create an alternative way to interact with the ALPINE Supercomputer, one that can happen in you internet browser like Chrome or Firefox. This method of accessing ALPINE is called OnDemand.

:hammer_and_wrench: **Group Exercise:** Let's practice accessing ALPINE using **OnDemand** together.

- Navigate to [OnDemand](https://ondemand-rmacc.rc.colorado.edu/) in a new tab or window
  - For me, I right click on the above link and select **Open Link in New Window**
  - You will be asked to select an identity provider using a pull-down menu. Select on the pull-down menu (it may say **ORCID**). Start typing **Colorado State University**. Click on **Remember** and log in. It should look like this

<p align="center">
<img width="75%" alt="login" src="../../05_images/login_window.png">
</p>

Next steps:
- Log into your CSU NET ID. You will receive a DUO PUSH on your phone. Accept it.
- To access the LINUX command line on ALPINE, go to the **Clusters** menu. Select **>_Alpine Shell**
- In another window, you can also access your files by going to the **Files** menu and selecting any available directories.

**Reflection:** How did this go for everyone? What problems were encountered?

Continue on to [Intro to ALPINE](3-5_Intro_to_Alpine.md)
