---
title: Microsoft Macro asembler BNF — Gramatyka
description: BNF opis MASM dla architektury x64.
ms.date: 12/17/2019
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), BNF reference
ms.openlocfilehash: 1a9577292e60db73838e5e6b850a4634db959fd6
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075464"
---
# <a name="microsoft-macro-assembler-bnf-grammar"></a>Microsoft Macro asembler BNF — Gramatyka

Ta strona zawiera opis BNF gramatycznej MASM. Jest on dostarczany jako uzupełnienie tematów referencyjnych i nie jest gwarantowany do ukończenia. Aby uzyskać pełne informacje dotyczące słów kluczowych, parametrów, operacji i tak dalej, zapoznaj się z tematami referencyjnymi.

Aby zilustrować użycie BNF, na poniższym diagramie przedstawiono definicję dyrektywy TYPEDEF, rozpoczynając od *typedefDir*nieterminala.

![Przykład MASM BNF](media/bnf.png)

Wpisy w poszczególnych nawiasach klamrowych to terminale (takie jak **NEAR16**, **NEAR32**, **FAR16**i **FAR32**) lub inne (takie jak *kwalifikator*, *kwalifikowanatype*, *odległość*i *protoSpec*), które można dodatkowo zdefiniować. Każdy kursywny niebędący w definicji *typedefDir* jest również wpisem w BNF. Trzy pionowe kropki wskazują definicję rozgałęziania dla nieterminalu, która w celu uproszczenia nie ilustruje tego rysunku.

Gramatyka BNF umożliwia używanie definicji cyklicznych. Na przykład Gramatyka używa kwalifikowanatype jako możliwej definicji dla kwalifikowanego, który jest również składnikiem definicji kwalifikatora. Symbol "|" określa wybór między wyrażeniami alternatywnymi, na przykład *endOfLine* | *komentarz*. Podwójne nawiasy klamrowe określają opcjonalny parametr, na przykład ⟦ *macroParmList* ⟧. Nawiasy w rzeczywistości nie pojawiają się w kodzie źródłowym.

## <a name="masm-nonterminals"></a>MASM inne niż terminale

*;;* \
&nbsp;&nbsp;&nbsp;&nbsp;*endOfLine* | *komentarz*

*= Dir*\
&nbsp;&nbsp;&nbsp;&nbsp;*id* = *immExpr* ;;

*addOp*\
&nbsp;&nbsp;&nbsp;&nbsp;+ | -

*aExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;*termin* | *aExpr* && *termin*

*altId*\
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*

*arbitraryText*\
&nbsp;&nbsp;&nbsp;&nbsp;*charlist*

*asmInstruction*\
&nbsp;&nbsp; *&nbsp;&nbsp;⟦* *exprList* ⟧

*assumeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**założono** *assumeList* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;| **założono nic** ;;

*assumeList*\
&nbsp;&nbsp;&nbsp;&nbsp;*assumeRegister* | *assumeList* , *assumeRegister*\

*assumeReg*\
&nbsp;&nbsp;&nbsp;&nbsp;*register* : *assumeVal*

*assumeRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;*assumeSegReg* | *assumeReg*

*assumeSegReg*\
&nbsp;&nbsp;&nbsp;&nbsp;*segmentRegister* : *assumeSegVal*

*assumeSegVal*\
&nbsp;&nbsp;&nbsp;&nbsp;*frameExpr* | **Nothing** | **błąd**

*assumeVal*\
&nbsp;&nbsp;&nbsp;&nbsp;*kwalifikowanatype* | **nie** | **błędu**

*bcdConst*\
&nbsp;&nbsp;&nbsp; *&nbsp;⟦ ⟧* *decNumber*

*binaryOp*\
&nbsp;&nbsp;&nbsp;&nbsp;= = |! = | > = | < = | > | < | &

*bitDef*\
&nbsp;&nbsp;&nbsp;&nbsp;*bitFieldId* : *BitFieldSize* ⟦ = *constExpr* ⟧

*bitDefList*\
&nbsp;&nbsp;&nbsp;&nbsp;*bitDef* | *bitDefList* , ⟦;; ⟧ *bitDef*

*bitFieldId*\
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*

*bitFieldSize*\
&nbsp;&nbsp;&nbsp;&nbsp;*constExpr*

*blockStatements*\
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList*\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. Kontynuuj** **. Jeśli** *cExpr* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. Przerwij** ⟦ **. Jeśli** *cExpr* ⟧

\ *bool*
&nbsp;&nbsp;&nbsp;&nbsp;**TRUE** | **false**

*byteRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;AL | AH | CL | CH | DL | ALGORYTM DH | BL | BH | R8B | R9B | R10B | R11B | R12B | R13B | R14B | R15B

*cExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;*aExpr* | *cExpr* || *aExpr*

\ *znaków*
&nbsp;&nbsp;&nbsp;&nbsp;dowolny znak z liczbą porządkową z zakresu 0 – 255 z wyjątkiem znaku wysuwu wiersza (10).

*charList*\
&nbsp;&nbsp;&nbsp;&nbsp;*znak* | *charlist*

*className*\
&nbsp;&nbsp;&nbsp;*ciągu* &nbsp;

*commDecl*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *nearfar* ⟧ ⟦ *langtype* ⟧ *ID* : *commtype*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦: *constExpr* ⟧

*commDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**communication**\
&nbsp;&nbsp;&nbsp;&nbsp;*commList* ;;

\ *komentarzy*
&nbsp;&nbsp;&nbsp;&nbsp;; *tekst* ;;

*commentDir*\
&nbsp;&nbsp;&nbsp;*ogranicznika* &nbsp;**komentarzy**\
&nbsp;&nbsp;&nbsp;&nbsp;*tekst*\
&nbsp;&nbsp;&nbsp;&nbsp;tekst *ogranicznika* *tekstu* *;;*

*commList*\
&nbsp;&nbsp;&nbsp;&nbsp;*commDecl* | *commList* , *commDecl*

\ *commtype*
&nbsp;&nbsp;&nbsp;&nbsp;*typ* | *constExpr*

\ *stała*
&nbsp;&nbsp;&nbsp;&nbsp;*cyfry* ⟦ *radixOverride* ⟧

\ *constExpr*
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie*

*contextDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**PUSHCONTEXT** *contextItemList* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;**POPCONTEXT** *contextItemList* ;;

*contextItem*\
&nbsp;&nbsp;&nbsp;&nbsp;**przyjęto** | **podstawy** | **listy** | **procesora** ** | **

*contextItemList*\
&nbsp;&nbsp;&nbsp;&nbsp;*contextItem* | *contextItemList* , *contextItem*

*controlBlock*\
&nbsp;&nbsp;&nbsp;&nbsp;*whileBlock* | *repeatBlock*

*controlDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*controlIf* | *controlBlock*

*controlElseif*\
&nbsp;&nbsp;&nbsp;&nbsp; **. &nbsp;ELSEIF** &nbsp;&nbsp;&nbsp;*cExpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList* \
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *controlElseif* ⟧

*controlIf*\
&nbsp;&nbsp;&nbsp;&nbsp; **. Jeśli** &nbsp;&nbsp;&nbsp;&nbsp;*cExpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *controlElseif* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦ **. ELSE** ;; \
&nbsp;&nbsp;&nbsp;&nbsp;[*directiveList*⟧ \
&nbsp;&nbsp;&nbsp;&nbsp; **. ENDIF** ;;

\ *współprocesorów*
&nbsp;&nbsp;&nbsp;&nbsp;. 8087 |. 287 |. 387 |. NO87

*crefDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*crefOption* ;;

*crefOption*\
&nbsp;&nbsp;&nbsp;&nbsp; **. CREF**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. XCREF** ⟦ *idList* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. NOCREF** ⟦ *idList* ⟧

*cxzExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie*\
&nbsp;&nbsp;&nbsp;&nbsp;|! \ *wyrażenia*
&nbsp;&nbsp;&nbsp;&nbsp;| *wyrażenie* = = Expr \
&nbsp;&nbsp;&nbsp;&nbsp;| *wyrażenie* ! = Expr

*dataDecl*\
&nbsp;&nbsp;&nbsp;&nbsp;DB | DW | DD | DF | ELEMENCIE DQ | DT | *Typ danych* | *typeId*

*dataDir*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *ID* ⟧ *;;*

*\ elementu* Ci
&nbsp;&nbsp;&nbsp;&nbsp;*dataDecl* *scalarInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;| *structTag* *structInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;| *typeId* *structInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;| *unionTag* *structInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;| *recordTag* *recordInstList*

*Typ danych*\
&nbsp;&nbsp;&nbsp;&nbsp;bajt | Brak SŁOWO | SWORD | DWORD | SDWORD | FWORD | WARTOŚĆ QWORD | SQWORD | TBYTE | OWORD | REAL4 | REAL8 | REAL10 | MMWORD | XMMWORD | YMMWORD

*decdigit*\
&nbsp;&nbsp;&nbsp;&nbsp;0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9

*decNumber*\
&nbsp;&nbsp;&nbsp;&nbsp;*decdigit*\
&nbsp;&nbsp;&nbsp;&nbsp;| *decNumber* *decdigit*

\ *ogranicznika*
&nbsp;&nbsp;&nbsp;&nbsp;dowolnego znaku z wyjątkiem *whiteSpaceCharacter*

*cyfry*\
&nbsp;&nbsp;&nbsp;&nbsp;*decdigit*\
&nbsp;&nbsp;&nbsp;&nbsp;| *cyfr* *decdigit*\
&nbsp;&nbsp;&nbsp;&nbsp;| *cyfr* hexdigit

\ *dyrektywy*
&nbsp;&nbsp;&nbsp;&nbsp;*generalDir* | *segmentDef*

*directiveList*\
&nbsp;&nbsp;&nbsp;&nbsp;*dyrektywa* | *directiveList* *directive*

\ *odległości*
&nbsp;&nbsp;&nbsp;&nbsp;*nearfar* | **NEAR16** | **NEAR32** | **FAR16** | **FAR32**

*e01*\
&nbsp;&nbsp;&nbsp;&nbsp;E01 *orOp* *E02* | *E02*

*e02*\
&nbsp;&nbsp;&nbsp;&nbsp;E02 **i** *E03* | *E03*

*e03*\
&nbsp;&nbsp; **&nbsp;&nbsp;** *E04* | *E04*

*e04*\
&nbsp;&nbsp;&nbsp;&nbsp;*E04* *relOp* *E05* | *E05*

*e05*\
&nbsp;&nbsp;&nbsp;&nbsp;*E05* *addOp* *E06* | *E06*

*e06*\
&nbsp;&nbsp;&nbsp;&nbsp;*E06* *mulOp* *e07* | *E06* *shiftOp* *E07* | *E07*

*e07*\
&nbsp;&nbsp;&nbsp;&nbsp;*E07* *addOp* *E08* | *E08*

*e08*\
&nbsp;&nbsp; **&nbsp;&nbsp;** *E09*\
&nbsp;&nbsp;&nbsp; **&nbsp;| ** *E09*\
&nbsp;&nbsp;&nbsp;&nbsp;| **HIGHWORD** *E09*\
&nbsp;&nbsp;&nbsp;&nbsp;| **LOWWORD** *E09*\
&nbsp;&nbsp;&nbsp;&nbsp;| *E09*

*e09*\
&nbsp;&nbsp;&nbsp;&nbsp;**przesunięcia** *E10*\
&nbsp;&nbsp;&nbsp;&nbsp;| **SEG** *E10*\
&nbsp;&nbsp;&nbsp;&nbsp;| **LROFFSET** *E10*\
&nbsp;&nbsp;&nbsp; **&nbsp;| ** *E10*\
&nbsp;&nbsp;&nbsp; **&nbsp;| ** *E10*\
&nbsp;&nbsp;&nbsp;&nbsp;| *E09* **PTR** *E10*\
&nbsp;&nbsp;&nbsp;&nbsp;| *E09* : *E10*\
&nbsp;&nbsp;&nbsp;&nbsp;| *E10*

*e10*\
&nbsp;&nbsp;&nbsp;&nbsp;*E10* . *e11*\
&nbsp;&nbsp;&nbsp;&nbsp;| *E10* ⟦ *Expr* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| *E11*

*e11*\
&nbsp;&nbsp;&nbsp;&nbsp;( *Expr* ) \
&nbsp;&nbsp;&nbsp;&nbsp;| ⟦ *Expr* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| **Szerokość** *\*
&nbsp;&nbsp;&nbsp;&nbsp;| **MASK** *Identyfikator* maski\
&nbsp;&nbsp;&nbsp; **&nbsp;| ** *sizeArg*\
&nbsp;&nbsp;&nbsp;&nbsp;| **SIZEOF** *sizeArg*\
&nbsp;&nbsp;&nbsp;&nbsp;*identyfikatorze* **długości** | \
&nbsp;&nbsp;&nbsp;&nbsp;| **LENGTHOF** *ID*\
&nbsp;&nbsp;&nbsp;&nbsp;| *recordConst*\
&nbsp;&nbsp;&nbsp;&nbsp;| *ciąg*\
&nbsp;&nbsp;&nbsp;&nbsp;| *stała*\
&nbsp;&nbsp;&nbsp; *&nbsp;| * \
&nbsp;&nbsp;&nbsp;&nbsp;| *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| **$**\
&nbsp;&nbsp;&nbsp;&nbsp;| *segmentRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;| *register*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ST**\
&nbsp;&nbsp;&nbsp;&nbsp;| **St** ( *wyrażenie* )

*echoDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**ECHO**\
&nbsp;&nbsp;&nbsp;&nbsp;*arbitraryText* ;; \
%**out** *arbitraryText* ;; \

*elseifBlock*\
&nbsp;&nbsp;&nbsp;&nbsp;*elseifStatement* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *elseifBlock* ⟧ \

*elseifStatement*\
&nbsp;&nbsp;&nbsp;&nbsp;**ElseIf** *constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFE** *constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFB** *textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFNB** *textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFDEF** *ID*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFNDEF** *ID*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFDIF** *textitem*\ *textItem*
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFDIFI** *textitem*\ *textItem*
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFIDN** *textitem*\ *textItem*
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFIDNI** *textitem*\ *textItem*
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIF1**\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIF2**

*endDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**End** ⟦ *immExpr* ⟧;;

*endpDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*procId* **ENDP** ;;

*endsDir*\
&nbsp;&nbsp;&nbsp;*identyfikator* **&nbsp;;;**

*equDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*textMacroId* **EQU** *equType* ;;

*equType*\
&nbsp;&nbsp;&nbsp;&nbsp;*immExpr* | *textliteral*

*errorDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*errorOpt* ;;

*errorOpt*\
&nbsp;&nbsp;&nbsp;&nbsp; **. ERR** ⟦ *textitem* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRE** *constExpr* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRNZ** *constExpr* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRB** *textitem* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRNB** *textitem* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRDEF** *ID* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRNDEF** *ID* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRDIF** *textitem* , *textitem* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRDIFI** *textitem* , *textitem* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRIDN** *textitem* , *textitem* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRIDNI** *textitem* , *textitem* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERR1** ⟦ *textitem* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERR2** ⟦ *textitem* ⟧

*exitDir*\
&nbsp;&nbsp;&nbsp;&nbsp; **. Zamknij** &nbsp;&nbsp;&nbsp;&nbsp;⟦ *Expr* ⟧;;

*exitmDir*\
&nbsp;&nbsp;&nbsp;&nbsp;: EXITM | EXITM *Textitem*

\ *wykładnika*
&nbsp;&nbsp;&nbsp; *&nbsp;⟦ ⟧* *decNumber*

\ *wyrażenia*
&nbsp;&nbsp;&nbsp;&nbsp;**Krótki** *E05*\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. E01 typu** \
&nbsp;&nbsp;&nbsp;&nbsp;| **OPATTR** *E01*\
&nbsp;&nbsp;&nbsp;&nbsp;| *E01*

*exprList*\
&nbsp;&nbsp;&nbsp;&nbsp;*expr* | *exprList* , *wyrażenie*

*externDef*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *langtype* ⟧ *ID* ⟦ ( *altId* ) ⟧: *externtype*

*externDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*externKey* *externList* ;;

*externKey*\
&nbsp;&nbsp;&nbsp;&nbsp;**EXTRN** | **extern** | **EXTERNDEF**

*externList*\
&nbsp;&nbsp;&nbsp;&nbsp;*externDef* | *externList* , ⟦;; ⟧ *externDef*

*unexterntype*\
&nbsp;&nbsp;&nbsp;&nbsp;**ABS** | *kwalifikowana*

*fieldAlign*\
&nbsp;&nbsp;&nbsp;&nbsp;*constExpr*

*fieldInit*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *initValue* ⟧ | *structInstance*

*fieldInitList*\
&nbsp;&nbsp;&nbsp;&nbsp;*fieldInit* | *fieldInitList* , ⟦;; ⟧ *fieldInit*

*fileChar*\
&nbsp;&nbsp;&nbsp;&nbsp;*ogranicznika*

*fileCharList*\
&nbsp;&nbsp;&nbsp;&nbsp;*fileChar* | *fileCharList* *fileChar*

*specyfikacja*\
&nbsp;&nbsp;&nbsp;&nbsp;*fileCharList* | *textliteral*

*flaganame*\
&nbsp;&nbsp;&nbsp;&nbsp;**zero?** | **przenieść?** | **przepełnienia?** | **podpisaniu?** | **parzystość?**

*floatNumber*\
&nbsp;&nbsp;&nbsp; *&nbsp;⟦ ⟧* *decNumber* . ⟦ *decNumber* ⟧ ⟦ *wykładnik* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| *cyfr* R | *cyfry* r

*forcDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**FORC** | **IRPC**

*forDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**dla** | **IRP**

*forParm*\
&nbsp;&nbsp;&nbsp;&nbsp;*ID* ⟦: *forParmType* ⟧

*forParmType*\
&nbsp;&nbsp;&nbsp;&nbsp;**REQ** | = *Textliteral*

*fpuRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;**St** *expr*

*frameExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;**SEG** *Identyfikator* SEG\
&nbsp;&nbsp;&nbsp;&nbsp;| **DGROUP** : *ID*\
&nbsp;&nbsp;&nbsp;&nbsp;| *segmentRegister* : *ID*\
&nbsp;&nbsp;&nbsp;&nbsp;*identyfikator* | 

*generalDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*modelDir* | *segOrderDir* | *nameDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *includeLibDir* | *commentDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *groupDir* | *assumeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *structDir* | *recordDir* | *typedefDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *externDir* | *publicDir* | *commDir* | *protoTypeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *equDir* | = Dir | *textDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *contextDir* | *optionDir* | *processorDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *radixDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *titleDir* | *pageDir* | *listDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *crefDir* | *echoDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *ifDir* | *errorDir* | *includeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *macroDir* | *macroCall* | *macroRepeat* | *purgeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *macroWhile* | *macroFor* | *macroForc*\
&nbsp;&nbsp;&nbsp;&nbsp;| *aliasDir*

*gpRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;AX | EAX | CX | ECX | DX | EDX | BX | EBX | DI | EDI | SI | ESI | BP | EBP | SP | ESP | ŻĄDANIE RSP | R8W | R8D | R9W | R9D | R12D | R13W | R13D | R14W | R14D

*groupDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*groupId* **grupy** GroupID *segIdList*

Identyfikator *groupId*\
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*

*hexdigit*\
&nbsp;&nbsp;&nbsp;&nbsp;b | c | d | e | f | A | B | C | D | E | N

*identyfikator*\
&nbsp;&nbsp;&nbsp;&nbsp;pierwszym znakiem identyfikatora może być wielkie lub małe litery alfabetu (`[A–Za-z]`) lub dowolne z czterech znaków: `@ _ $ ?` pozostałe znaki mogą być tymi samymi znakami lub cyfrą dziesiętną (`[0–9]`). Maksymalna długość to 247 znaków.

*idList*\
&nbsp;&nbsp;&nbsp;&nbsp;*id* | *idList* , *ID*

*ifDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*ifStatement* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *elseifBlock* ⟧ \
&nbsp;&nbsp;&nbsp; **&nbsp;⟦** \
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList* ⟧;; \

*ifStatement*\
&nbsp;&nbsp;&nbsp;&nbsp;, **Jeśli** wyrażenie *constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| **Ife** *constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFB** *textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFNB** *textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ifdef** *ID*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ifndef** *ID*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFDIF** *textitem*\ *textItem*
&nbsp;&nbsp;&nbsp;&nbsp;| **IFDIFI** *textitem*\ *textItem*
&nbsp;&nbsp;&nbsp;&nbsp;| **IFIDN** *textitem*\ *textItem*
&nbsp;&nbsp;&nbsp;&nbsp;| **IFIDNI** *textitem*\ *textItem*
&nbsp;&nbsp;&nbsp;&nbsp;| **IF1**\
&nbsp;&nbsp;&nbsp;&nbsp;| **IF2**

*immExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie*

*includeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**Uwzględnij** *Specyfikacja* ;;

*includeLibDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**includelib —** *Specyfikacja* ;;

*initValue*\
&nbsp;&nbsp;&nbsp;&nbsp;*immExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| *ciąg*\
&nbsp;&nbsp;&nbsp;&nbsp;|? \
&nbsp;&nbsp;&nbsp;&nbsp;| *constExpr* **DUP** ( *scalarInstList* ) \
&nbsp;&nbsp;&nbsp;&nbsp;| *floatNumber*\
&nbsp;&nbsp;&nbsp;&nbsp;| *bcdConst*

*inSegDir*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *labelDef* ⟧ *inSegmentDir*

*inSegDirList*\
&nbsp;&nbsp;&nbsp;&nbsp;*inSegDir* | *inSegDirList* *inSegDir*

*inSegmentDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*instrukcji*\
&nbsp;&nbsp;&nbsp;&nbsp;| *dataDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *controlDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *startupDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *exitDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *offsetDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *labelDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *procDir* ⟦ *LocalDirList* ⟧ ⟦ *inSegDirList* ⟧ *endpDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *invokeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *generalDir*

*instrPrefix*\
&nbsp;&nbsp;&nbsp;&nbsp;**REP** | **REPE** | **REPZ** | **REPNE** | **REPNZ** | **Lock**

\ *instrukcji*
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *instrPrefix* ⟧ *asmInstruction*

*invokeArg*\
&nbsp;&nbsp;&nbsp;&nbsp;*register* :: *register* | *wyrażenie* | **adresu** *expr*

*invokeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**Wywołaj** *wyrażenie* ⟦, ⟦;; ⟧ *invokeList* ⟧;;

*invokeList*\
&nbsp;&nbsp;&nbsp;&nbsp;*invokeArg* | *invokeList* , ⟦;; ⟧ *invokeArg*

\ *słów kluczowych*
&nbsp;&nbsp;&nbsp;&nbsp;słowa zastrzeżone.

*keywordList*\
&nbsp;&nbsp;&nbsp;&nbsp;*słowo kluczowe* * | * *keywordList*

*labelDef*\
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator* : | *Identyfikator* :: | @@:

*labelDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator* **LABEL** *kwalifikowana* ;;

\ *langtype*
&nbsp;&nbsp;&nbsp;&nbsp;**C** | **PASCAL** | **pascal** | **Basic** | **syscall** | **stdcall**

*listDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*listOption* ;;

*listOption*\
&nbsp;&nbsp;&nbsp;&nbsp; **.\ listy**
&nbsp;&nbsp;&nbsp;&nbsp;|  **. Nolist**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. XLIST**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. LISTALL**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. LISTIF**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. LFCOND**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. NOLISTIF**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. SFCOND**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. TFCOND**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. LISTMACROALL** |  **. LALL**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. NOLISTMACRO** |  **. SALL**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. LISTMACRO** |  **. XALL**\

*localDef*\
&nbsp;&nbsp;&nbsp;&nbsp;**lokalnego** *idList* ;;

*localDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**lokalnego** *parmList* ;;

*localDirList*\
&nbsp;&nbsp;&nbsp;&nbsp;*localDir* | *localDirList* *localDir*

*localList*\
&nbsp;&nbsp;&nbsp;&nbsp;*localDef* | *localList* *localDef*

*macroArg*\
 % *constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| %*textMacroId*\
&nbsp;&nbsp;&nbsp;&nbsp;| %*macroFuncId* ( *macroArgList* ) \
&nbsp;&nbsp;&nbsp;&nbsp;| *ciąg*\
&nbsp;&nbsp;&nbsp;&nbsp;| *arbitraryText*\
&nbsp;&nbsp;&nbsp;&nbsp;| < *arbitraryText* >

*macroArgList*\
&nbsp;&nbsp;&nbsp;&nbsp;*macroArg* | *macroArgList* , *macroArg*

*macroBody*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *localList* ⟧ *macroStmtList*

*macroCall*\
&nbsp;&nbsp;&nbsp;&nbsp;*ID* *macroArgList* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;| *ID* ( *macroArgList* )

*macroDir*\
&nbsp;&nbsp; *&nbsp;&nbsp;,* **makro** ⟦ *macroParmList* ⟧;; \
&nbsp;&nbsp;&nbsp;&nbsp;*macroBody*\
&nbsp;&nbsp;&nbsp;&nbsp;**ENDM** ;;

*macroFor*\
&nbsp;&nbsp;&nbsp;&nbsp;*forDir* *ForParm* , < *macroArgList* >;; \
&nbsp;&nbsp;&nbsp;&nbsp;*macroBody*\
&nbsp;&nbsp;&nbsp;&nbsp;**ENDM** ;;

*macroForc*\
&nbsp;&nbsp;&nbsp;&nbsp;*forcDir* *Identyfikator* forcDir, *textliteral* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*macroBody*\
&nbsp;&nbsp;&nbsp;&nbsp;**ENDM** ;;

*macroFuncId*\
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*

*macroId*\
&nbsp;&nbsp;&nbsp;&nbsp;*macroProcId* | *macroFuncId*

*macroIdList*\
&nbsp;&nbsp;&nbsp;&nbsp;*macroId* | *macroIdList* , *macroId*

*macroLabel*\
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*

*macroParm*\
&nbsp;&nbsp;&nbsp;&nbsp;*ID* ⟦: *parmType* ⟧

*macroParmList*\
&nbsp;&nbsp;&nbsp;&nbsp;*macroParm* | *macroParmList* , ⟦;; ⟧ *macroParm*

*macroProcId*\
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*

*macroRepeat*\
&nbsp;&nbsp;&nbsp;&nbsp;*repeatDir* *constExpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*macroBody*\
&nbsp;&nbsp;&nbsp;&nbsp;**ENDM** ;;

*macroStmt*\
&nbsp;&nbsp;&nbsp;&nbsp;*dyrektywa* \
&nbsp;&nbsp;&nbsp;&nbsp;| *exitmDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| : *macroLabel*\
&nbsp;&nbsp;&nbsp;&nbsp;| **GOTO**\
&nbsp;&nbsp;&nbsp;&nbsp;*macroLabel*

*macroStmtList*\
&nbsp;&nbsp;&nbsp;&nbsp;*macroStmt* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;| *macroStmtList* *macroStmt* ;; \

*macroWhile*\
&nbsp;&nbsp;&nbsp;&nbsp;**podczas** *constExpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*macroBody*\
&nbsp;&nbsp;&nbsp;&nbsp;**ENDM** ;;

*mapType*\
&nbsp;&nbsp;&nbsp;&nbsp;**wszystkie** | **Brak** | **NOTPUBLIC**

*memOption*\
&nbsp;&nbsp; **&nbsp;&nbsp;niewielka | ** **mała** | **średnia** | **Compact** | **duże** | ogromny ** | ** **HUGE**

*\*
&nbsp;&nbsp;&nbsp;&nbsp;Nazwa instrukcji.

*modelDir*\
&nbsp;&nbsp;&nbsp;&nbsp; **.\ modelu**
&nbsp;&nbsp;&nbsp;&nbsp;*memOption* ⟦, *modelOptlist* ⟧;;

*modelOpt*\
&nbsp;&nbsp;&nbsp;&nbsp;*langtype* | *stackOption*

*modelOptlist*\
&nbsp;&nbsp;&nbsp;&nbsp;*modelOpt* | *modelOptlist* , *modelOpt*

\ *modułu*
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *directiveList* ⟧ *endDir*

*mulOp*\
&nbsp;&nbsp;&nbsp;&nbsp;\* | / | **Mod**

*nameDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**nazwa**\
&nbsp;&nbsp;&nbsp;&nbsp;*ID* ;; \

*nearfar*\
&nbsp;&nbsp;&nbsp;&nbsp;**blisko** | **daleko**

*nestedStruct*\
&nbsp;&nbsp;&nbsp;&nbsp;*structHdr* ⟦ *ID* ⟧;; \
&nbsp;&nbsp;&nbsp;&nbsp;*structBody*\
&nbsp;&nbsp;&nbsp;&nbsp;**zakończeniu** ;; \

*offsetDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*offsetDirType* ;;

*offsetDirType*\
&nbsp;&nbsp;&nbsp;&nbsp;**nawet** | **org** *immExpr* | **align** ⟦ *constExpr* ⟧

*przesunięciatype*\
&nbsp;&nbsp;&nbsp;&nbsp;**grupy** | **segmentu** | **płaski**

*oldRecordFieldList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *constExpr* ⟧ | *oldRecordFieldList* , ⟦ *constExpr* ⟧

*optionDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**opcji** *optionList* ;;

*optionItem*\
&nbsp;&nbsp;&nbsp;&nbsp;**CASEMAP** : *mapType*\
&nbsp;&nbsp;&nbsp;&nbsp;| **DOTNAME** | **NODOTNAME**\
&nbsp;&nbsp;&nbsp;&nbsp;| **EMULATOR** | **noemulator**\
&nbsp;&nbsp;&nbsp;&nbsp;| **epilogu** : *macroId*\
&nbsp;&nbsp;&nbsp;&nbsp;| **EXPR16** | **EXPR32**\
&nbsp;&nbsp;&nbsp;&nbsp;| **Language** : *langtype*\
&nbsp;&nbsp;&nbsp;&nbsp;| **LJMP**
| **NOLJMP**\
&nbsp;&nbsp;&nbsp;&nbsp;| **M510** | **NOM510**\
&nbsp;&nbsp;&nbsp;&nbsp;| **NOSŁOWO kluczowe** : < *keywordList* >\
&nbsp;&nbsp;&nbsp;&nbsp;| **NOSIGNEXTEND**\
&nbsp;&nbsp;&nbsp;&nbsp;| **przesunięcie** : *OffsetType*\
&nbsp;&nbsp;&nbsp;&nbsp;| **OLDMACROS** | **NOOLDMACROS**\
&nbsp;&nbsp;&nbsp;&nbsp;| **OLDSTRUCTS** | **NOOLDSTRUCTS**\
&nbsp;&nbsp;&nbsp;&nbsp;| **proc** : *oVisibility*\
&nbsp;&nbsp;&nbsp;&nbsp;| **prologu** : *macroId*\
&nbsp;&nbsp;&nbsp;&nbsp;| **READONLY** | **noreadonly**\
&nbsp;&nbsp;&nbsp;&nbsp;| **zakresie** | **nieobjętych zakresem**\
&nbsp;&nbsp;&nbsp;&nbsp;| **segment** : *segSize*\
&nbsp;&nbsp;&nbsp;&nbsp;| **SETIF2** : bool

*optionList*\
&nbsp;&nbsp;&nbsp;&nbsp;*optionItem* | *optionList* , ⟦;; ⟧ *optionItem*

*optText*\
&nbsp;&nbsp;&nbsp;&nbsp;, *Textitem*

*orOp*\
&nbsp;&nbsp;&nbsp;&nbsp;**lub** | **XOR**

*oVisibility*\
&nbsp;&nbsp;&nbsp;&nbsp;**publiczny** | **prywatny** | **eksport**

*pageDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**str** ⟦ *pageExpr* ⟧;;

*pageExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;\+ | ⟦ *pageLength* ⟧ ⟦, *PageWidth* ⟧

*pageLength*\
&nbsp;&nbsp;&nbsp;&nbsp;*constExpr*

*pageWidth*\
&nbsp;&nbsp;&nbsp;&nbsp;*constExpr*

*parametr*\
&nbsp;&nbsp;&nbsp;&nbsp;*parmId* ⟦: *kwalifikowanatype* ⟧ | *parmId* ⟦ *constExpr* ⟧ ⟦: *kwalifikowanatype* ⟧

*parmId*\
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*

*parmList*\
&nbsp;&nbsp;&nbsp;&nbsp;*parametr* | *parmList* , ⟦;; ⟧ *parametr*

*parmType*\
&nbsp;&nbsp;&nbsp;&nbsp;**REQ** | = *textliteral* | **vararg**

*pOptions*\
&nbsp;&nbsp;&nbsp; *&nbsp;⟦ ⟧* ⟦ *langtype* *⟧ ⟦ oVisibility ⟧*

\ *podstawowe*
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenia* *binaryOp* *wyrażenie* | *flaganame* | *wyrażenie*

*procDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*procId* **proc**\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *pOptions* ⟧ ⟦ < *macroArgList* > ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *usesRegs* ⟧ ⟦ *procParmList* ⟧

\ *procesora*
&nbsp;&nbsp;&nbsp;&nbsp;|. 386 |. 386P |. 486 |. 486P \
&nbsp;&nbsp;&nbsp;&nbsp;|. 586 |. 586P |. 686 |. 686P |. 387

*processorDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*procesor* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;| *współprocesorem* ;;

*procId*\
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*

*procItem*\
&nbsp;&nbsp;&nbsp;&nbsp;*instrPrefix* | *dataDir* | *labelDir* | *offsetDir* | *generalDir*

*procParmList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦, ⟦;; ⟧ *parmList* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦, ⟦;; ⟧ *parmId* : vararg ⟧

*protoArg*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *ID* ⟧: *kwalifikowanatype*

*protoArgList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦, ⟦;; ⟧ *protoList* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦, ⟦;; ⟧ ⟦ *ID* ⟧: vararg ⟧

*protoList*\
&nbsp;&nbsp;&nbsp;&nbsp;*protoArg*\
&nbsp;&nbsp;&nbsp;&nbsp;| *protoList* , ⟦;; ⟧ *protoArg*

*protoSpec*\
&nbsp;&nbsp;&nbsp; *&nbsp;⟦ ⟧* ⟦ *langtype* *⟧ ⟦ protoArgList ⟧ |* *Identyfikator* elementu

*protoTypeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*ID* **proto** *protoSpec*

*pubDef*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *langtype* ⟧ *id*

*publicDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**Public** *pubList* ;;

*pubList*\
&nbsp;&nbsp;&nbsp;&nbsp;*pubDef* | *pubList* , ⟦;; ⟧ *pubDef*

*purgeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**przeczyszczanie** *macroIdList*

*kwalifikowana* -\
&nbsp;&nbsp;&nbsp;&nbsp;*Typ* | ⟦ *Distance* ⟧ **PTR** ⟦ *kwalifikowanatype* ⟧

\ *kwalifikatora*
&nbsp;&nbsp;&nbsp;&nbsp;*kwalifikowanatype* | **proto** *protoSpec*

\ *cytatu*
&nbsp;&nbsp;&nbsp;&nbsp;"|"

*qwordRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;RAX | RCX | RDX | RBX | RDI | RSI | RBP | R8 | R9 | R10 | R11 | R12 | R13 | R14 | R15

*radixDir*\
&nbsp;&nbsp;&nbsp;&nbsp; **. PODSTAWY** *constExpr* ;;

*radixOverride*\
&nbsp;&nbsp;&nbsp;&nbsp;h | o | p | t | t | H | O | P | T | T

*recordConst*\
&nbsp;&nbsp;&nbsp;&nbsp;*recordTag* { *oldRecordFieldList* } | *recordTag* < *oldRecordFieldList* >

*recordDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*recordTag* **Record** *bitDefList* ;;

*recordFieldList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *constExpr* ⟧ | *recordFieldList* , ⟦;; ⟧ ⟦ *constExpr* ⟧

*recordInstance*\
 {⟦;; ⟧ *recordFieldList* ⟦;; ⟧} \
&nbsp;&nbsp;&nbsp;&nbsp;| < *oldRecordFieldList* >\
&nbsp;&nbsp;&nbsp;&nbsp;| *constExpr* **DUP** ( *recordInstance* )

*recordInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;*recordInstance* | *recordInstList* , ⟦;; ⟧ *recordInstance*

*recordTag*\
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*

*zarejestruj*\
&nbsp;&nbsp;&nbsp;&nbsp;*specialRegister* | *gpRegister* | *byteRegister* | *qwordRegister* |  *fpuRegister* | *SIMDRegister* | *segmentRegister*

*regList*\
&nbsp;&nbsp;&nbsp;&nbsp;*register* | *regList* *register*

*relOp*\
&nbsp;&nbsp;&nbsp;&nbsp;EQ | NE | LT | LE | GT | STRON

*repeatBlock*\
&nbsp;&nbsp;&nbsp;&nbsp; **. Powtórz** ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*blockStatements* ;; untilDir ;;

*repeatDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**powtarzaj** | **powt**

*scalarInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;*initValue* | *scalarInstList* , ⟦;; ⟧ *initValue*

*segAlign*\
&nbsp;&nbsp;&nbsp;&nbsp;**bajt** | **Word** | **DWORD** | **para** | **PAGE**

*segAttrib*\
&nbsp;&nbsp;&nbsp;&nbsp;**PUBLIC** | **Stack** | **Common** | **Memory** | **w** obszarze *constExpr* | **Private**

*segDir*\
&nbsp;&nbsp;&nbsp;&nbsp; **.\ kodu**
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *segId* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **.\ danych**
&nbsp;&nbsp;&nbsp;&nbsp;|   **. DANE?** \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. STAŁA**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. FARDATA**⟦ *segId* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|   **. FARDATA?** ⟦ *segId* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. STACK** ⟦ *constExpr* ⟧

*segId*\
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*

*segIdList*\
&nbsp;&nbsp;&nbsp;&nbsp;*segId*\
&nbsp;&nbsp;&nbsp;&nbsp;| *segIdList* , *segId*

*segmentDef*\
&nbsp;&nbsp;&nbsp;&nbsp;*segmentDir* ⟦ *inSegDirList* ⟧ *endsDir* | *simpleSegDir* ⟦ *inSegDirList* ⟧ ⟦ *endsDir* ⟧

*segmentDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*segId* **⟦** *segOptionList* ⟧;;

*segmentRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;**CS** | **DS** | **ES** | **FS** | **GS** | **SS**

*segOption*\
&nbsp;&nbsp;&nbsp;&nbsp;*segAlign*\
&nbsp;&nbsp;&nbsp;&nbsp;| *segRO*\
&nbsp;&nbsp;&nbsp;&nbsp;| *segAttrib*\
&nbsp;&nbsp;&nbsp;&nbsp;| *segSize*\
&nbsp;&nbsp;&nbsp;&nbsp;| *ClassName*

*segOptionList*\
&nbsp;&nbsp;&nbsp;&nbsp;*segOption* | *segOptionList* *segOption*

*segOrderDir*\
&nbsp;&nbsp;&nbsp;&nbsp; **.**  | Alpha **. SEQ** |  **. DOSSEG —**  | **dosseg —**

*segRO*\
&nbsp;&nbsp;&nbsp;&nbsp;**tylko do odczytu**

*segSize*\
&nbsp;&nbsp;&nbsp;&nbsp;**USE16** | **USE32** | **Flat**

*shiftOp*\
&nbsp;&nbsp;&nbsp;&nbsp;**SHR** | **SHL**

*Podpisz*\
 - | +

*simdRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;MM0 | MM1 | MM2 | MM3 | MM4 | MM5 | MM6 | MM7 | xmmRegister | YMM0 | YMM1 | YMM2 | YMM3 | YMM4 | YMM5 | YMM6 | YMM7 | YMM8 | YMM9 | YMM10 | YMM11 | YMM12 | YMM13 | YMM14 | YMM15

*simpleExpr*\
 ( *cExpr* ) | *podstawowa*

*simpleSegDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*segDir* ;;

*sizeArg*\
&nbsp;&nbsp;&nbsp;&nbsp;*identyfikator* |  * | * *E10*

*specialChars*\
 : | . | ⟦ | ⟧ | ( | ) | < | > | { | } \
&nbsp;&nbsp;&nbsp;&nbsp;| + | - | / | * | & | % | !\
&nbsp;&nbsp;&nbsp;&nbsp;| "| \ | = | ; | , | "\
&nbsp;&nbsp;&nbsp;&nbsp;| *whiteSpaceCharacter*\
&nbsp;&nbsp;&nbsp;&nbsp;| *endOfLine*

*specialRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;CR0 | CR2 | CR3 | DR0 | DR1 | DR2 | DR3 | DR6 | DR7 | TR3 | TR4 | TR5 | TR6 | TR7

*stackOption*\
&nbsp;&nbsp;&nbsp;&nbsp;**NEARSTACK** | **FARSTACK**

*startupDir*\
&nbsp;&nbsp;&nbsp;&nbsp; **. Uruchamianie** ;;

*stext*\
&nbsp;&nbsp;&nbsp;&nbsp;*stringChar* | *stext* *stringChar*

*ciąg*\
&nbsp;&nbsp;&nbsp;&nbsp;*cytat* ⟦ *stext* ⟧ *quote*

*stringChar*\
&nbsp;&nbsp;&nbsp;&nbsp;oferta *oferty* *|* Dowolny znak z wyjątkiem cudzysłowu.

*structBody*\
&nbsp;&nbsp;&nbsp;&nbsp;*structItem* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;| *structBody* *structItem* ;;

*structDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*structTag* *structHdr* ⟦ *fieldAlign* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦, **nieunikatowy** ⟧;; \
&nbsp;&nbsp;&nbsp;&nbsp;*structBody*\
&nbsp;&nbsp;&nbsp;&nbsp;*structTag*\
&nbsp;&nbsp;&nbsp;&nbsp;**zakończeniu** ;;

*structHdr*\
&nbsp;&nbsp;&nbsp;&nbsp;**STRUC** | **struct** | **Union**

*structInstance*\
 < ⟦ *fieldInitList* ⟧ > \
&nbsp;&nbsp;&nbsp;&nbsp;| {⟦;; ⟧ ⟦ *fieldInitList* ⟧ ⟦;; ⟧} \
&nbsp;&nbsp;&nbsp;&nbsp;| *constExpr* **DUP** ( *structInstList* ) \

*structInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;*structInstance* | *structInstList* , ⟦;; ⟧ *structInstance*

*structItem*\
&nbsp;&nbsp;&nbsp;&nbsp;*dataDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *generalDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *offsetDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *nestedStruct*

*structTag*\
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*

\ *warunku*
&nbsp;&nbsp;&nbsp;&nbsp;*simpleExpr* |! *simpleExpr*

\ *tekstu*
&nbsp;&nbsp;&nbsp;&nbsp;*textliteral* | znak *tekstu* |! *znak | * *znaku |* ! *character* *znak*

*textDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*ID* *textMacroDir* ;;

*element textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;*textliteral* | *textMacroId* | % *constExpr*

*textLen*\
&nbsp;&nbsp;&nbsp;&nbsp;*constExpr*

\ *Textlist*
&nbsp;&nbsp;&nbsp;&nbsp;*textitem* | *textlist* , ⟦;; ⟧ *Textitem*

\ *Textliteral*
&nbsp;&nbsp;&nbsp;&nbsp;< *tekst* >;;

*textMacroDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**catStr —** ⟦ *textlist* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| **TEXTEQU** ⟦ *textlist* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| **sizestr —** *textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **substr** *textitem* , *textstart* ⟦, *textLen* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| **instr** ⟦ *textstart* , ⟧ *textitem* , *textitem*

*textMacroId*\
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*

\ *Textstart*
&nbsp;&nbsp;&nbsp;&nbsp;*constExpr*

*titleDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*titletype* *arbitraryText* ;;

*nazwa*\
&nbsp;&nbsp;&nbsp;&nbsp;**tytuł** | **podtytuł** | **SUBTTL**

*typ*\
&nbsp;&nbsp;&nbsp;&nbsp;*structTag*\
&nbsp;&nbsp;&nbsp;&nbsp;| *unionTag*\
&nbsp;&nbsp;&nbsp;&nbsp;| *recordTag*\
&nbsp;&nbsp;&nbsp; *&nbsp;| * \
&nbsp;&nbsp;&nbsp;&nbsp;| *dataType*\
&nbsp;&nbsp;&nbsp;&nbsp;| *typeId*

*typedefDir*\
&nbsp;&nbsp;&nbsp;&nbsp;kwalifikator elementu *typeId* **typedef**

\ *typeId*
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*

*unionTag*\
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*

*untilDir*\
&nbsp;&nbsp;&nbsp;&nbsp; **. DO** *cExpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp; **. UNTILCXZ** ⟦ *cxzExpr* ⟧;;

*usesRegs*\
&nbsp;&nbsp;&nbsp;&nbsp;**używa** *regList*

*whileBlock*\
&nbsp;&nbsp;&nbsp;&nbsp; **. PODCZAS**\
&nbsp;&nbsp;&nbsp;&nbsp;*cExpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*blockStatements* ;; \
&nbsp;&nbsp;&nbsp;&nbsp; **. ENDW**

*whiteSpaceCharacter*\
&nbsp;&nbsp;&nbsp;&nbsp;ASCII 8, 9, 11 – 13, 26, 32

*xmmRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;XMM0 | XMM1 | XMM2 | XMM3 | XMM4 | XMM5 | XMM6 | XMM7 | XMM8 | XMM9 | XMM10 | XMM11 | XMM12 | XMM13 | XMM14 | XMM15\
