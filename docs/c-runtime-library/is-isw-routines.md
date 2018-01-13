---
title: "jest isw — procedury | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- isw
- is
dev_langs: C++
helpviewer_keywords:
- is routines
- isw routines
ms.assetid: 1e171a57-2cde-41f6-a75f-a080fa3c12e5
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fa1cc76bf925a334b78e5f15565c089081cfe9d1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="is-isw-routines"></a>is, isw — Procedury
|||  
|-|-|  
|[isalnum, iswalnum, _isalnum_l, _iswalnum_l](../c-runtime-library/reference/isalnum-iswalnum-isalnum-l-iswalnum-l.md)|[isgraph, iswgraph, _isgraph_l, _iswgraph_l](../c-runtime-library/reference/isgraph-iswgraph-isgraph-l-iswgraph-l.md)|  
|[isalpha, iswalpha, _isalpha_l, _iswalpha_l](../c-runtime-library/reference/isalpha-iswalpha-isalpha-l-iswalpha-l.md)|[isleadbyte, _isleadbyte_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|  
|[isascii, __isascii, iswascii](../c-runtime-library/reference/isascii-isascii-iswascii.md)|[islower, iswlower, _islower_l, _iswlower_l](../c-runtime-library/reference/islower-iswlower-islower-l-iswlower-l.md)|  
|[isblank, iswblank, _isblank_l, _iswblank_l](../c-runtime-library/reference/isblank-iswblank-isblank-l-iswblank-l.md)|[isprint, iswprint, _isprint_l, _iswprint_l](../c-runtime-library/reference/isprint-iswprint-isprint-l-iswprint-l.md)|  
|[iscntrl, iswcntrl, _iscntrl_l, _iswcntrl_l](../c-runtime-library/reference/iscntrl-iswcntrl-iscntrl-l-iswcntrl-l.md)|[ispunct, iswpunct, _ispunct_l, _iswpunct_l](../c-runtime-library/reference/ispunct-iswpunct-ispunct-l-iswpunct-l.md)|  
|[iscsym —, iscsymf —, __iscsym —, \__iswcsym, \__iscsymf, \__iswcsymf, _iscsym_l —, _iswcsym_l —, _iscsymf_l —, _iswcsymf_l —](../c-runtime-library/reference/iscsym-functions.md)|[isspace, iswspace, _isspace_l, _iswspace_l](../c-runtime-library/reference/isspace-iswspace-isspace-l-iswspace-l.md)|  
|[_isctype, iswctype, _isctype_l, _iswctype_l](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)|[isupper, _isupper_l, iswupper, _iswupper_l](../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md)|  
|[isdigit, iswdigit, _isdigit_l, _iswdigit_l](../c-runtime-library/reference/isdigit-iswdigit-isdigit-l-iswdigit-l.md)|[isxdigit, iswxdigit, _isxdigit_l, _iswxdigit_l](../c-runtime-library/reference/isxdigit-iswxdigit-isxdigit-l-iswxdigit-l.md)|  
  
## <a name="remarks"></a>Uwagi  
 Te procedury testu znaków dla określonych warunków.  
  
 **Jest** procedury uzyskanie znaczących wyników argumentu liczba całkowita od -1 (`EOF`) do **uchar_max —** (0xFF) włącznie. Typu oczekiwanego argumentu jest `int`.  
  
> [!CAUTION]
>  Aby uzyskać **jest** procedury przekazywaniem argumentu typu `char` może dać nieoczekiwane wyniki. SBCS i MBCS znaków jednobajtowych typu `char` o wartości większej niż 0x7F jest ujemna. Jeśli `char` jest przekazywany, kompilator może przekonwertować wartości zalogowany `int` lub zalogowany **długi**. Ta wartość może być znakiem przez kompilator, nieoczekiwane wyniki.  
  
 **Isw —** procedury uzyskanie znaczących wyników dla dowolną liczbą całkowitą z zakresu od - 1 (**weof —**) do 0xFFFF włącznie. **Wint_t —** — typ danych jest zdefiniowany w WCHAR. H jako **niepodpisane krótko**; go może zawierać żadnych znaków dwubajtowych lub znaków dwubajtowych koniec pliku (**weof —**) wartość.  
  
 Wartość wyjściowa jest zagrożony ustawienie `LC_CTYPE` ustawienie kategorii ustawień regionalnych; zobacz [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji bez **_l** Użyj sufiksu bieżące ustawienia regionalne tego zachowania zależnych od ustawień regionalnych; wersje z **_l** sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych Przekazano zamiast tego.  
  
 Zgodnie z ustawieniami regionalnymi "C", testu warunki dotyczące **jest** procedury są następujące:  
  
 `isalnum`  
 Alfanumeryczne (- Z, - z lub 0 - 9).  
  
 `isalpha`  
 Litery (A - Z lub a - z).  
  
 `__isascii`  
 Znaków ASCII (0x00 - 0x7F).  
  
 `isblank`  
 Poziomy tab lub miejsca na znak (0x09 lub 0x20).  
  
 `iscntrl`  
 Kontrolowanie znaków (0x00-0x1F lub 0x7F).  
  
 `__iscsym`  
 Litera, podkreślenie lub cyfra.  
  
 `__iscsymf`  
 Litery lub podkreślenia.  
  
 **isdigit —**  
 Cyfrę (0 - 9).  
  
 `isgraph`  
 Drukowalnych znaku z wyjątkiem spacji ().  
  
 `islower`  
 Małe litery (- z).  
  
 `isprint`  
 Znaków drukowalnych tym miejsca (0x20 - 0x7E).  
  
 `ispunct`  
 Znak interpunkcyjny.  
  
 `isspace`  
 Biały znak (0x09-0x0D lub 0x20).  
  
 `isupper`  
 Wielkie litery (- Z).  
  
 `isxdigit`  
 Szesnastkowa (A - F, - f lub 0 - 9).  
  
 Aby uzyskać **isw —** procedury, wynik testu dla określonego warunku jest niezależna od ustawień regionalnych. Test warunki dotyczące **isw —** dostępne są następujące funkcje:  
  
 `iswalnum`  
 `iswalpha`lub `iswdigit`.  
  
 `iswalpha`  
 Znaków dwubajtowych, który jest jednym z zestawu zdefiniowane w implementacji, dla których żadna `iswcntrl`, `iswdigit`, `iswpunct`, lub `iswspace` jest różna od zera. `iswalpha`Zwraca niezerową tylko w przypadku znaki dwubajtowe, dla którego `iswupper` lub `iswlower` jest różna od zera.  
  
 `iswascii`  
 Reprezentacja znaków dwubajtowych znaków ASCII (0x0000 - 0x007F).  
  
 `iswblank`  
 Szerokość znaku odpowiada standardowe spacją lub jeden zestaw znaki dwubajtowe, dla którego zdefiniowane w implementacji `iswalnum` ma wartość false. Miejsca są standardowe pustych znaków (L "") i tabulator poziomy (L "\t").  
  
 `iswcntrl`  
 Formant znaków dwubajtowych.  
  
 **__iswcsym —**  
 Dowolny znak szerokości, dla którego **isalnum —** jest wartość PRAWDA lub znakiem "_".  
  
 **__iswcsymf —**  
 Dowolny znak szerokości, dla którego `iswalpha` jest wartość PRAWDA lub znakiem "_".  
  
 `iswctype`  
 Znak ma określona przez właściwość `desc` argumentu. Dla każdego prawidłowa wartość `desc` argument `iswctype`, brak procedury klasyfikacji znaków dwubajtowych równoważne, jak pokazano w poniższej tabeli:  
  
 **Równoważność (iswctype —**   
 ***c, desc* ) do innych isw — procedury testowania**  
  
|Wartość *desc* argumentu|iswctype — ( *c, desc* ) równoważne|  
|------------------------------|----------------------------------------|  
|**_ALPHA**|**iswalpha — (** `c` **)**|  
|**_ALPHA** &#124; **_DIGIT**|**iswalnum — (** `c` **)**|  
|**_BLANK**|**iswblank (** `c` **)**|  
|**STE_ROWANIA**|**iswcntrl — (** `c` **)**|  
|**_DIGIT**|**iswdigit — (** `c` **)**|  
|**_ALPHA** &#124; **_DIGIT** &#124; **_PUNCT**|**iswgraph — (** `c` **)**|  
|**_LOWER**|**iswlower — (** `c` **)**|  
|**_ALPHA** &#124; **_BLANK** &#124; **_DIGIT** &#124; **_PUNCT**|**iswprint — (** `c` **)**|  
|**_PUNCT**|**iswpunct — (** `c` **)**|  
|**_BLANK**|**iswblank (** `c` **)**|  
|**_SPACE**|**iswspace — (** `c` **)**|  
|**_UPPER**|**iswupper — (** `c` **)**|  
|**_HEX**|**iswxdigit — (** `c` **)**|  
  
 `iswdigit`  
 Znaków dwubajtowych odpowiadający znakowi cyfr dziesiętnych.  
  
 `iswgraph`  
 Drukowalnych znaków dwubajtowych z wyjątkiem miejsca wielu znaków (L "").  
  
 `iswlower`  
 Małe litery, lub jeden z zdefiniowane w implementacji zestaw znaki dwubajtowe dla których żadna `iswcntrl`, `iswdigit`, `iswpunct`, lub `iswspace` jest różna od zera. `iswlower`Zwraca wartość niezerową tylko w przypadku znaki dwubajtowe, które odpowiadają na małe litery.  
  
 `iswprint`  
 Drukowalnych znaków dwubajtowych, w tym miejsca szerokość znaku (L "").  
  
 `iswpunct`  
 Drukowalnych znaków dwubajtowych będący ani miejsca szerokość znaku (L "") ani całego znak, dla którego `iswalnum` jest różna od zera.  
  
 `iswspace`  
 Szerokość znaku odpowiada standardowe biały znak lub jest zdefiniowane w implementacji zestawu z znaki dwubajtowe, dla którego `iswalnum` ma wartość false. Standardowa białe znaki są: miejsca (L ""), wysuwu strony (L "\f"), znaków nowego wiersza (L "\n"), powrotu karetki (L "\r"), tabulator poziomy (L "\t") i tabulator pionowy (L "\v").  
  
 `iswupper`  
 Szerokość znaku które wielkie lub jeden zestaw znaki dwubajtowe, dla których żadna zdefiniowane w implementacji `iswcntrl`, `iswdigit`, `iswpunct`, lub `iswspace` jest różna od zera. `iswupper`Zwraca niezerową tylko w przypadku znaki dwubajtowe, które odpowiadają na wielkie litery.  
  
 `iswxdigit`  
 Znaków typu Wide umożliwiająca cyfrę szesnastkową.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_isfam.c  
/* This program tests all characters between 0x0  
 * and 0x7F, then displays each character with abbreviations  
 * for the character-type codes that apply.  
 */  
  
#include <stdio.h>  
#include <ctype.h>  
  
int main( void )  
{  
   int ch;  
   for( ch = 0; ch <= 0x7F; ch++ )  
   {  
      printf( "%.2x  ", ch );  
      printf( " %c", isprint( ch )  ? ch   : ' ' );  
      printf( "%4s", isalnum( ch )  ? "AN" : "" );  
      printf( "%3s", isalpha( ch )  ? "A"  : "" );  
      printf( "%3s", __isascii( ch )  ? "AS" : "" );  
      printf( "%3s", iscntrl( ch )  ? "C"  : "" );  
      printf( "%3s", __iscsym( ch )  ? "CS "  : "" );  
      printf( "%3s", __iscsymf( ch )  ? "CSF"  : "" );  
      printf( "%3s", isdigit( ch )  ? "D"  : "" );  
      printf( "%3s", isgraph( ch )  ? "G"  : "" );  
      printf( "%3s", islower( ch )  ? "L"  : "" );  
      printf( "%3s", ispunct( ch )  ? "PU" : "" );  
      printf( "%3s", isspace( ch )  ? "S"  : "" );  
      printf( "%3s", isprint( ch )  ? "PR" : "" );  
      printf( "%3s", isupper( ch )  ? "U"  : "" );  
      printf( "%3s", isxdigit( ch ) ? "X"  : "" );  
      printf( ".\n" );  
   }  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
00            AS  C                              .  
01            AS  C                              .  
02            AS  C                              .  
03            AS  C                              .  
04            AS  C                              .  
05            AS  C                              .  
06            AS  C                              .  
07            AS  C                              .  
08            AS  C                              .  
09            AS  C                    S         .  
0a            AS  C                    S         .  
0b            AS  C                    S         .  
0c            AS  C                    S         .  
0d            AS  C                    S         .  
0e            AS  C                              .  
0f            AS  C                              .  
10            AS  C                              .  
11            AS  C                              .  
12            AS  C                              .  
13            AS  C                              .  
14            AS  C                              .  
15            AS  C                              .  
16            AS  C                              .  
17            AS  C                              .  
18            AS  C                              .  
19            AS  C                              .  
1a            AS  C                              .  
1b            AS  C                              .  
1c            AS  C                              .  
1d            AS  C                              .  
1e            AS  C                              .  
1f            AS  C                              .  
20            AS                       S PR      .  
21   !        AS              G    PU    PR      .  
22   "        AS              G    PU    PR      .  
23   #        AS              G    PU    PR      .  
24   $        AS              G    PU    PR      .  
25   %        AS              G    PU    PR      .  
26   &        AS              G    PU    PR      .  
27   '        AS              G    PU    PR      .  
28   (        AS              G    PU    PR      .  
29   )        AS              G    PU    PR      .  
2a   *        AS              G    PU    PR      .  
2b   +        AS              G    PU    PR      .  
2c   ,        AS              G    PU    PR      .  
2d   -        AS              G    PU    PR      .  
2e   .        AS              G    PU    PR      .  
2f   /        AS              G    PU    PR      .  
30   0  AN    AS   CS      D  G          PR     X.  
31   1  AN    AS   CS      D  G          PR     X.  
32   2  AN    AS   CS      D  G          PR     X.  
33   3  AN    AS   CS      D  G          PR     X.  
34   4  AN    AS   CS      D  G          PR     X.  
35   5  AN    AS   CS      D  G          PR     X.  
36   6  AN    AS   CS      D  G          PR     X.  
37   7  AN    AS   CS      D  G          PR     X.  
38   8  AN    AS   CS      D  G          PR     X.  
39   9  AN    AS   CS      D  G          PR     X.  
3a   :        AS              G    PU    PR      .  
3b   ;        AS              G    PU    PR      .  
3c   <        AS              G    PU    PR      .  
3d   =        AS              G    PU    PR      .  
3e   >        AS              G    PU    PR      .  
3f   ?        AS              G    PU    PR      .  
40   @        AS              G    PU    PR      .  
41   A  AN  A AS   CS CSF     G          PR  U  X.  
42   B  AN  A AS   CS CSF     G          PR  U  X.  
43   C  AN  A AS   CS CSF     G          PR  U  X.  
44   D  AN  A AS   CS CSF     G          PR  U  X.  
45   E  AN  A AS   CS CSF     G          PR  U  X.  
46   F  AN  A AS   CS CSF     G          PR  U  X.  
47   G  AN  A AS   CS CSF     G          PR  U   .  
48   H  AN  A AS   CS CSF     G          PR  U   .  
49   I  AN  A AS   CS CSF     G          PR  U   .  
4a   J  AN  A AS   CS CSF     G          PR  U   .  
4b   K  AN  A AS   CS CSF     G          PR  U   .  
4c   L  AN  A AS   CS CSF     G          PR  U   .  
4d   M  AN  A AS   CS CSF     G          PR  U   .  
4e   N  AN  A AS   CS CSF     G          PR  U   .  
4f   O  AN  A AS   CS CSF     G          PR  U   .  
50   P  AN  A AS   CS CSF     G          PR  U   .  
51   Q  AN  A AS   CS CSF     G          PR  U   .  
52   R  AN  A AS   CS CSF     G          PR  U   .  
53   S  AN  A AS   CS CSF     G          PR  U   .  
54   T  AN  A AS   CS CSF     G          PR  U   .  
55   U  AN  A AS   CS CSF     G          PR  U   .  
56   V  AN  A AS   CS CSF     G          PR  U   .  
57   W  AN  A AS   CS CSF     G          PR  U   .  
58   X  AN  A AS   CS CSF     G          PR  U   .  
59   Y  AN  A AS   CS CSF     G          PR  U   .  
5a   Z  AN  A AS   CS CSF     G          PR  U   .  
5b   [        AS              G    PU    PR      .  
5c   \        AS              G    PU    PR      .  
5d   ]        AS              G    PU    PR      .  
5e   ^        AS              G    PU    PR      .  
5f   _        AS   CS CSF     G    PU    PR      .  
60   `        AS              G    PU    PR      .  
61   a  AN  A AS   CS CSF     G  L       PR     X.  
62   b  AN  A AS   CS CSF     G  L       PR     X.  
63   c  AN  A AS   CS CSF     G  L       PR     X.  
64   d  AN  A AS   CS CSF     G  L       PR     X.  
65   e  AN  A AS   CS CSF     G  L       PR     X.  
66   f  AN  A AS   CS CSF     G  L       PR     X.  
67   g  AN  A AS   CS CSF     G  L       PR      .  
68   h  AN  A AS   CS CSF     G  L       PR      .  
69   i  AN  A AS   CS CSF     G  L       PR      .  
6a   j  AN  A AS   CS CSF     G  L       PR      .  
6b   k  AN  A AS   CS CSF     G  L       PR      .  
6c   l  AN  A AS   CS CSF     G  L       PR      .  
6d   m  AN  A AS   CS CSF     G  L       PR      .  
6e   n  AN  A AS   CS CSF     G  L       PR      .  
6f   o  AN  A AS   CS CSF     G  L       PR      .  
70   p  AN  A AS   CS CSF     G  L       PR      .  
71   q  AN  A AS   CS CSF     G  L       PR      .  
72   r  AN  A AS   CS CSF     G  L       PR      .  
73   s  AN  A AS   CS CSF     G  L       PR      .  
74   t  AN  A AS   CS CSF     G  L       PR      .  
75   u  AN  A AS   CS CSF     G  L       PR      .  
76   v  AN  A AS   CS CSF     G  L       PR      .  
77   w  AN  A AS   CS CSF     G  L       PR      .  
78   x  AN  A AS   CS CSF     G  L       PR      .  
79   y  AN  A AS   CS CSF     G  L       PR      .  
7a   z  AN  A AS   CS CSF     G  L       PR      .  
7b   {        AS              G    PU    PR      .  
7c   |        AS              G    PU    PR      .  
7d   }        AS              G    PU    PR      .  
7e   ~        AS              G    PU    PR      .  
7f            AS  C                              .  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Klasyfikacja znaków](../c-runtime-library/character-classification.md)   
 [Ustawienia regionalne](../c-runtime-library/locale.md)   
 [setLocale, _wsetlocale —](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [Interpretacja wielobajtowych sekwencji znaków](../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [to, funkcje](../c-runtime-library/to-functions.md)