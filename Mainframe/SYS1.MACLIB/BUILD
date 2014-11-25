*/*                                                                  */ 00002000
*/*PROPRIETARY V3 STATEMENT                                          */ 00004000
*/*LICENSED MATERIALS - PROPERTY OF IBM                              */ 00006000
*/*"RESTRICTED MATERIALS OF IBM"                                     */ 00008000
*/*5695-DF1                                                          */ 00010000
*/*(C) COPYRIGHT 1992  IBM CORP.                                     */ 00012000
*/*END PROPRIETARY V3 STATEMENT                                      */ 00015000
*/*                                                                  */ 00018000
         MACRO                                                          00020000
&NAME    BUILD &POOL,&NO,&LTH,&DUMMY=                                   00030000
         LCLB  &NOGO                                                    00040000
         AIF   ('&POOL' EQ '').E1                                       00060000
.R1      ANOP                                                           00070000
         AIF   ('&NO' EQ '').E2                                         00080000
.R2      AIF   ('&NO' EQ '(0)').T1                                      00085000
         AIF   ('&LTH' EQ '').E3                                        00090000
.R3      AIF   (&NOGO EQ 1).TERM                                        00095000
&NAME    IHBINNRA &POOL                                                 00100000
         AIF   ('&LTH' EQ '&LTH(1)' AND '&NO' EQ '&NO(1)').CONT         00120000
         AIF   ('&NO' EQ '&NO(1)').NUMB                                 00140000
         AIF   ('&NO' EQ '(0)').ZERO                                    00160000
         STH   &NO(1),0(0,1)                     STORE BUFFER NUMBER    00180000
         AGO   .CHKLTH                                                  00200000
.ZERO    ST    &NO(1),0(0,1)                     STORE PARAMETERS       00220000
         AGO   .LINK                                                    00240000
.NUMB    AIF   (T'&NO NE 'N').USEDC                                     00260000
         AIF   (&NO GT 4095).USEDC                                      00280000
         LA    14,&NO.(0,0)                      GET BUFFER NUMBER      00300000
         STH   14,0(0,1)                         STORE INTO LIST        00320000
         AGO   .CHKLTH                                                  00340000
.USEDC   B     *+6                               BRANCH AROUND VALUE    00360000
         DC    AL2(&NO)                          NUMBER OF BUFFERS      00380000
         MVC   0(2,1),*-2                        STORE INTO LIST        00400000
.CHKLTH  AIF   ('&NO' EQ '(0)').LINK                                    00420000
         AIF   ('&LTH' EQ '').E3                                        00440000
         AIF   ('&LTH' EQ '&LTH(1)').NUMBL                              00460000
         STH   &LTH(1),2(0,1)                    STORE BUFFER LENGTH    00480000
         AGO   .LINK                                                    00500000
.NUMBL   AIF   (T'&LTH NE 'N').USEDCL                                   00520000
         AIF   (&LTH GT 4095).USEDCL                                    00540000
         LA    14,&LTH.(0,0)                     GET BUFFER LENGTH      00560000
         STH   14,2(0,1)                         STORE IN LIST          00580000
         AGO   .LINK                                                    00600000
.USEDCL  B     *+6                               BRANCH AROUND VALUE    00620000
         DC    AL2(&LTH)                         LENGTH OF BUFFERS      00640000
         MVC   2(2,1),*-2                        STORE INTO LIST        00660000
         AGO   .LINK                                                    00680000
.CONT    AIF   ('&LTH' EQ '').E3                                        00700000
         B     *+8                               BRANCH AROUND VALUES   00720000
         DC    AL2(&NO)                          NUMBER OF BUFFERS      00740000
         DC    AL2(&LTH)                         LENGTH OF BUFFERS      00760000
         MVC   0(4,1),*-4                        MOVE INTO LIST         00780000
.LINK    LINK  EP=IECBBFB1                                              00800000
         MEXIT                                                          00820000
.E1      IHBERMAC 02                                                    00830000
&NOGO    SETB  1                                                        00848000
         AGO   .R1                                                      00856000
.T1      AIF   ('&LTH' NE '').E4                                        00864000
         AGO   .R3                                                      00872000
.E2      IHBERMAC 03                                                    00880000
&NOGO    SETB  1                                                        00888000
         AGO   .R2                                                      00896000
.E4      IHBERMAC 38,,&LTH                                              00904000
         MEXIT                                                          00912000
.E3      IHBERMAC 04                                                    00921000
.TERM    ANOP                                                           00930000
         MEND                                                           00940000
