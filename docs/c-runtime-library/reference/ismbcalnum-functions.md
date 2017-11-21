---
title: "_ismbcalnum —, _ismbcalnum_l —, _ismbcalpha —, _ismbcalpha_l —, _ismbcdigit —, _ismbcdigit_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ismbcalpha
- _ismbcalnum
- _ismbcdigit
- _ismbcalnum_l
- _ismbcdigit_l
- _ismbcalpha_l
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _ismbcdigit
- ismbcalnum_l
- _ismbcdigit_l
- _ismbcalpha
- ismbcalnum
- ismbcdigit
- ismbcalpha
- _ismbcalnum_l
- _ismbcalnum
- ismbcdigit_l
dev_langs: C++
helpviewer_keywords:
- ismbcalpha function
- _ismbcalnum function
- ismbcdigit_l function
- _ismbcalnum_l function
- _ismbcdigit function
- ismbcalnum function
- _ismbcalpha_l function
- ismbcdigit function
- _ismbcalpha function
- _ismbcdigit_l function
- ismbcalnum_l function
- ismbcalpha_l function
ms.assetid: 12d57925-aebe-46e0-80b0-82b84c4c31ec
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3ad428851bd89dd2e9efd49a900ccdc28066b246
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ismbcalnum-ismbcalnuml-ismbcalpha-ismbcalphal-ismbcdigit-ismbcdigitl"></a>_ismbcalnum, _ismbcalnum_l, _ismbcalpha, _ismbcalpha_l, _ismbcdigit, _ismbcdigit_l
Sprawdza, czy jest alfanumeryczne znaków wielobajtowych, alfa lub cyfra.  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
int _ismbcalnum  
(  
   unsigned int c   
);  
int _ismbcalnum_l  
(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbcalpha  
(  
   unsigned int c   
);  
int _ismbcalpha_l  
(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbcdigit  
(  
   unsigned int c   
);  
int _ismbcdigit_l  
(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `c`  
 Znak do sprawdzenia.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Każdy z tych procedur zwraca wartość różną od zera, jeśli znak spełnia warunek testu lub 0, jeśli jej nie ma. Jeśli `c`< = 255 i ma odpowiadającego `_ismbb` procedura (na przykład `_ismbcalnum` odpowiada `_ismbbalnum`), wynik jest zwracana wartość odpowiadającego `_ismbb` procedury.  
  
## <a name="remarks"></a>Uwagi  
 Każdy z tych procedur testy danego znaków wielobajtowych dla podanego warunku.  
  
 Wersje tych funkcji z `_l` sufiks są identyczne, z wyjątkiem tego, aby były używane ustawienia regionalne przekazana zamiast bieżące ustawienia regionalne dla ich działania zależnego od ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
|Procedura|Stan testu|Przykład kodu strony 932|  
|-------------|--------------------|---------------------------|  
|`_ismbcalnum,_ismbcalnum_l`|Alfanumeryczne|Zwraca różną od zera w przypadku i tylko wtedy, gdy `c` odzwierciedla jednobajtowe litery angielskie ASCII: Zobacz przykłady `_ismbcdigit` i `_ismbcalpha`.|  
|`_ismbcalpha,_ismbcalpha_l`|Alfabetyczne|Zwraca wartość niezerową w przypadku i tylko wtedy, gdy `c` odzwierciedla jednobajtowe litery angielskie ASCII: 0x41 < =`c`< = 0x5A lub 0x61 < =`c`< = 0x7A; lub list katakana: 0xA6 < =`c`< = 0xDF.|  
|`_ismbcdigit,_ismbcdigit`|Cyfra|Zwraca wartość niezerową w przypadku i tylko wtedy, gdy `c` odzwierciedla jednobajtowe cyfr ASCII: 0x30 < =`c`< = 0x39.|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_ismbcalnum,_ismbcalnum_l`|\<mbstring.h >|  
|`_ismbcalpha,_ismbcalpha_l`|\<mbstring.h >|  
|`_ismbcdigit,_ismbcdigit_l`|\<mbstring.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasyfikacja znaków](../../c-runtime-library/character-classification.md)   
 [_ismbc — procedury](../../c-runtime-library/ismbc-routines.md)   
 [jest isw — procedury](../../c-runtime-library/is-isw-routines.md)   
 [_ismbb — procedury](../../c-runtime-library/ismbb-routines.md)