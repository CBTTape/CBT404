# CBT404
Converted to GitHub via [cbt2git](https://github.com/wizardofzos/cbt2git)

This is still a work in progress. 
Due to amazing work by Alison Zhang and Jake Choi repos are no longer deleted.

```
//***FILE 404 is source for TSSO to be run under OS/390 and z/OS.   *   FILE 404
//*                                                                 *   FILE 404
//*       Updated by John McKown to no longer require that the      *   FILE 404
//*       TSSOPARM member be in SYS1.PARMLIB, but it uses the       *   FILE 404
//*       IEFPRMLB service to search the PARMLIB concatenation      *   FILE 404
//*       of libraries.  Optionally, you can include a //PARMLIB    *   FILE 404
//*       DD card in the TSSO proc, to point to the library of      *   FILE 404
//*       your choice.                                              *   FILE 404
//*                                                                 *   FILE 404
//*    A WORD-format version of the TSSO 4.3 doc is included here   *   FILE 404
//*    courtesy of John Kalinich, as member $TSSODOC.               *   FILE 404
//*                                                                 *   FILE 404
//*    ---------------------------------------------------------    *   FILE 404
//*                                                                 *   FILE 404
//*    Fixed for z/OS 1.8 elimination of the Master Console,        *   FILE 404
//*    and to accommodate only 4-byte console ids.  Fix is by       *   FILE 404
//*    Larry Lawler (aka Dr CICS).                                  *   FILE 404
//*                                                                 *   FILE 404
//*    Old version (z/OS 1.7 and before) has been packaged in       *   FILE 404
//*    PDSLOAD format, as member $$PREZ18.  To reconstitute the     *   FILE 404
//*    old install pds, just run job $PDSLOAD in this pds, which    *   FILE 404
//*    is self-contained, and will yield the old pds for File 404.  *   FILE 404
//*                                                                 *   FILE 404
//*    Also added were newer versions of the "assemble all" and     *   FILE 404
//*    "assemble one module" JCL streams.  These are members:       *   FILE 404
//*                                                                 *   FILE 404
//*    ASMA9ALL and ASMA9ONE                                        *   FILE 404
//*                                                                 *   FILE 404
//*    A suggested enhancement which shows (at TSSO initialization  *   FILE 404
//*    time) which subsystem consoles are present, is included      *   FILE 404
//*    as member $$ENHANC.  You can use this extra source for       *   FILE 404
//*    this enhancement, if you want to.  It also comes from        *   FILE 404
//*    Larry Lawler.                                                *   FILE 404
//*                                                                 *   FILE 404
//*    ---------------------------------------------------------    *   FILE 404
//*                                                                 *   FILE 404
//*    Major modifications have been made to this version by        *   FILE 404
//*    Ed Jaffe.  Fixes were also added by Dave Cartwright.         *   FILE 404
//*    This version now should run on the z/OS releases which       *   FILE 404
//*    are available now (11/02).  Dependencies are on ESA 4.1      *   FILE 404
//*    and higher.                                                  *   FILE 404
//*                                                                 *   FILE 404
//*    Some fixes were made by Peter Vander Woude.  Please check    *   FILE 404
//*    over member $PVWNOTE.                                        *   FILE 404
//*                                                                 *   FILE 404
//*        email: "Peter Vander Woude" <pwoude@harristeeter.com>    *   FILE 404
//*                                                                 *   FILE 404
//*    Fixes made to TSSOSS09 by Michael Mayne and Daniel Cattin.   *   FILE 404
//*                                                                 *   FILE 404
//*        email:  mmayne@chattanooga.net    mmayne@hhsys.org       *   FILE 404
//*                Cattin@osys.ch                                   *   FILE 404
//*                                                                 *   FILE 404
//*    This version contains a fix to SPMON from Brian Westerman,   *   FILE 404
//*    so it doesn't get an 0C4.  See member $$SPMON for details.   *   FILE 404
//*                                                                 *   FILE 404
//*        email:  Brian_Westerman@SyzygyInc.com                    *   FILE 404
//*                                                                 *   FILE 404
//*    Note.  For older versions of TSSO (Bellcore version),        *   FILE 404
//*           please see Files 247, 248, 249 of the CBT Overflow    *   FILE 404
//*           Tape.  The mapping from the former files on this      *   FILE 404
//*           tape is as follows:                                   *   FILE 404
//*                                                                 *   FILE 404
//*   File 401 - Original Bellcore version ---> File 247 (Overflow) *   FILE 404
//*   File 402 - Dave Cartwright's updates ---> File 248 (Overflow) *   FILE 404
//*   File 403 - DC updates fitted to F401 ---> File 249 (Overflow) *   FILE 404
//*   File 404 - Previous version on File 404 > File 250 (Overflow) *   FILE 404
//*                                                                 *   FILE 404
//*           Bill Godfrey's original version of TSSO is still      *   FILE 404
//*           on File 306 of the CBT MVS Utilities Tape.            *   FILE 404
//*                                                                 *   FILE 404
//*           The Time Sharing Subsystem Option (TSSO) is a         *   FILE 404
//*           package designed to increase operator productivity    *   FILE 404
//*           by automating tasks which need not be performed       *   FILE 404
//*           manually.  TSSO performs its function through three   *   FILE 404
//*           integrated components.  The Operator Productivity     *   FILE 404
//*           Facility (OPF) extends the power of TSO to the        *   FILE 404
//*           MVS operator's console.  The Automated Operations     *   FILE 404
//*           Facility (AOF) enhances an installation's             *   FILE 404
//*           ability to control system events based on console     *   FILE 404
//*           message traffic.  An interface to the Network         *   FILE 404
//*           Communication Control Facility (NCCF) allows the      *   FILE 404
//*           network operator to use TSSO as a command processor,  *   FILE 404
//*           issuing and receiving operating system commands at    *   FILE 404
//*           the NCCF terminal.  Note that NCCF is now an inte-    *   FILE 404
//*           grated part of Netview.  TSSO also enhances end-user  *   FILE 404
//*           productivity by allowing end-user access to the MVS   *   FILE 404
//*           Command Subsystem.  A complete User's Guide,          *   FILE 404
//*           including detailed installation instructions exists   *   FILE 404
//*           in member UG43TERM in this file.                      *   FILE 404
//*                                                                 *   FILE 404
//*           A guide to the new features of TSSO Version 4,        *   FILE 404
//*           Release 3 is in the member RELGDE43 in this file.     *   FILE 404
//*                                                                 *   FILE 404
//*           Anyone with an interest in automated operations is    *   FILE 404
//*           invited to look at TSSO as a software tool providing  *   FILE 404
//*           many of the primitives required for common automated  *   FILE 404
//*           operations tasks.  These primitives include the       *   FILE 404
//*           hilighting, lowlighting, replying and reacting to     *   FILE 404
//*           operating system messages.  This is in addition to    *   FILE 404
//*           the ability to issue a command and retrieve the       *   FILE 404
//*           response in CLIST variables.                          *   FILE 404
//*                                                                 *   FILE 404
//* --------------------------------------------------------------  *   FILE 404
//*                                                                 *   FILE 404
//*      Note on Dave Cartwright's modifications:                   *   FILE 404
//*                                                                 *   FILE 404
//*         The purpose of these modifications is to allow TSSO     *   FILE 404
//*         to handle automated message processing with multi-      *   FILE 404
//*         line WTO's and to do other new functions.  File 402     *   FILE 404
//*         has been merged into TSSO 4.3 by Guy Albertelli.  So    *   FILE 404
//*         it's probably best to ignore File 402 and install       *   FILE 404
//*         File 404 instead, which is an OS/390 upgrade of the     *   FILE 404
//*         former File 403.  As noted above, the former Files      *   FILE 404
//*         401 thru 403 have been moved to the CBT Overflow Tape.  *   FILE 404
//*                                                                 *   FILE 404
//* --------------------------------------------------------------  *   FILE 404
//*      Small change to TSSOWTO to fix a vulnerability.            *   FILE 404
//* --------------------------------------------------------------  *   FILE 404
//*                                                                 *   FILE 404
//*           THIS FILE IS IN IEBUPDTE SYSIN FORMAT.                *   FILE 404
//*                                                                 *   FILE 404
//*           QUESTIONS, PLEASE CONTACT Sam Golob:                  *   FILE 404
//*                      sbgolob@cbttape.org                        *   FILE 404
//*                                                                 *   FILE 404
```
