Mainframe source code is in the "Mainframe" folder (directory).
Listing are in "Assemblies".

The source includes the macro-libraries used to assemble.
Note that each folder in "Mainframe" is associated with
a mainframe library or dataset with the following naming
convention:

Library/dataset name         folder/dataset
WYL.gg.uuu.dataset           gg.uuu/dataset
WYL.gg.uuu.library#member    gg.uuu/library/member

Examples:
WYL.GA.PUB.ERRORS            GA.PUB/ERRORS
WYL.GA.PUB.WYLHELP           GA.PUB/WYLHELP
WYL.GG.PUB.INTDOC            GG.PUB/INTDOC
WYL.GQ.PUB.BATWYL.TXT        GQ.PUB/BATWYL.TXT
WYL.GS.MIL.MILTEN.MACLIB     GS.MIL/MILTEN.MACLIB
WYL.GS.MIL.MILTEN.SOURCE     GS.MIL/MILTEN.SOURCE
WYL.GS.WYL.WYLBUR.MACLIB     GS.WYL/WYLBUR.MACLIB
WYL.GS.WYL.WINGS.PARMS       GS.WYL/WINGS/PARMS
WYL.GA.PUB.WYLHELP           GA.PUB/WYLHELP

All of the SYS1 and SYS3 folders have names which exactly
match their equivalent mainframe library dataset names.

DIRINFO lists all directory names in Mainframe.
DIRLIBS lists all "library" dataset names.

The AMY#ASM.txt file in Assemblies is a listing of
AMELIA - the NETWORK ACCESS INTERFACE.  However, source
code and maclibs are not provided for either AMELIA or
the assembler.  The assembler (ASMA90) is in TESTASM,
which is an IEBCOPY unloaded dataset (VS/6160/6164).

NOTE: All files are written as plain TEXT files in ASCII
with Unix-style line endings (x'0a').  Although creator
is set to ttxt (TextEdit), the files should be readable by
any text editor (vi, xedit, BBEdit, etc.).  Note that all
data went through EBCDIC to ASCII conversions, so imbedded
special characters like x'FF' might be X'07' instead.

When placed on a mainframe, they should be card-image
datasets (LRECL=80) or Edit-format datasets (RECFM=U).
Read GG.PUB/INTDOC/EDITFMT for description of Edit-format.
See the Assemblies listings for what macro-libraries go
with various sources.

WINGS

The WINGS folder contains all the source for WINGS, the
OS interface to datasets for both WYLBUR and ORVYL.
There is a "readme.txt" inside that explains more.

SYS3.USERMODS.SOURCE

This folder contains source code for several MVS alterations
to SVCs, such as the "Suzan SVC" (aka: SVCCOMM).  This is the
inter-region communications package that allows WYLBUR to pass
commands to ORVYL, etc.  This is also how WYLBUR and ORVYL do
their communications with WINGS.  SYS3.USERMODS.DIRINFO contains
a complete "SHOW DIRECTORY" output for SYS3.USERMODS.SOURCE
