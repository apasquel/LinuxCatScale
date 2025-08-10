# Linux-CatScale IR Collection Script 

Linux CatScale is a bash script that uses living off the land tools to collect extensive data from Linux based hosts. The data aims to help DFIR, Threat Hunters, and Blue Team professionals triage and scope incidents. An ELK Stack logstash conf is provided to consume the output and assist the analysis process. 

## Attention
📢 This version of Cat-Scale is an updated fork of the original project by FSecure. This version includes bug fixes and updates deprecated bash options to improve reliability and functionality. 

- [Usage](#usage)
- [Parsing](#parsing)
- [What does it Collect](#what-does-it-collect)
- [Disclaimer](#disclaimer)
- [Tested OSes](#tested-oses)

## Usage

This scripts were built to automate as much as possible. For forensic captures, it is recommended to run this from an external drive or usb to minimize impact to the target system. However, it can be run over SSH against remote hosts.  

Please run the collection script on suspected hosts with sudo rights. Cat-Scale.sh is the only file you need. 

```
user@suspecthost:<dir>$ chmod +x ./Cat-Scale.sh
user@suspecthost:<dir>$ sudo ./Cat-Scale.sh 
```

The script will create a directory called "CatScale-out" in the working directory and should remove all artefacts after being compressed. This will leave a filename in the format of `Hostname-YYMMDD-HHMM.tar.gz` 

Once these are all aggregated and you have the `Hostname-YYMMDD-HHMM.tar.gz` on the analysis machine. You can run Extract-Cat-Scale.sh which will extract all the files and place them in a folder called "extracted".

```
user@analysishost:<dir>$ chmod +x ./Extract-Cat-Scale.sh
user@analysishost:<dir>$ sudo ./Extract-Cat-Scale.sh
```

### Parsing

This project has predefined grok filters to ingest data into elastic, feel free to modify them as you need. 

## What does it collect?

This script will produce output and archive. Currently most up to date what it collects is covered in the blog post here: https://labs.withsecure.com/tools/cat-scale-linux-incident-response-collection

## Disclaimer

Note that the script will likely alter artifacts on endpoints. Care should be taken when using the script. This is not meant to take forensically sound disk images of the remote endpoints. However the script can be used for triage and threat hunting purposes. 

## Tested OSes

- Ubuntu 16.4
- Red Hat Enterprise Linux 8
- Centos/Rocky 
- Mint
- Solaris 11.4