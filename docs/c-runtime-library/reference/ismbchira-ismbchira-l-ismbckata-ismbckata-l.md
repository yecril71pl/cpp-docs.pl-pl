---
title: "_ismbchira —, _ismbchira_l —, _ismbckata —, _ismbckata_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ismbckata
- _ismbchira_l
- _ismbchira
- _ismbckata_l
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
- ismbckata_l
- _ismbckata_l
- ismbckata
- ismbchira
- _ismbckata
- ismbchira_l
- _ismbchira_l
- _ismbchira
dev_langs: C++
helpviewer_keywords:
- _ismbckata function
- _ismbchira function
- _ismbckata_l function
- Katakana
- ismbchira function
- _ismbchira_l function
- ismbchira_l function
- ismbdkata_l function
- Hiragana
- ismbckata function
ms.assetid: 2db388a2-be31-489b-81c8-f6bf3f0582d3
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b0e257ac4a1998e75fc47e719df2163d49654c71
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ismbchira-ismbchiral-ismbckata-ismbckatal"></a>_ismbchira, _ismbchira_l, _ismbckata, _ismbckata_l
**Funkcje właściwe 932 strony kodu**  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
int _ismbchira(  
   unsigned int c   
);  
int _ismbchira_l(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbckata(  
   unsigned int c   
);  
int _ismbckata_l(  
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
 Każdy z tych procedur zwraca wartość różną od zera, jeśli znak spełnia warunek testu lub 0, jeśli jej nie ma. Jeśli `c` < = 255 i ma odpowiadającego `_ismbb` procedura (na przykład `_ismbcalnum` odpowiada `_ismbbalnum`), wynik jest zwracana wartość odpowiadającego `_ismbb` procedury.  
  
## <a name="remarks"></a>Uwagi  
 Każda z tych funkcji testy danego znaków wielobajtowych dla podanego warunku.  
  
 Wersje tych funkcji z `_l` sufiks są identyczne, z wyjątkiem tego, aby były używane ustawienia regionalne przekazana zamiast bieżące ustawienia regionalne dla ich działania zależnego od ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
|Procedura|Testowanie warunku (strona kodowa 932 tylko)|  
|-------------|-------------------------------------------|  
|`_ismbchira`|Hiragana znaków dwubajtowych: 0x829F < =`c`< = 0x82F1.|  
|`_ismbchira_l`|Hiragana znaków dwubajtowych: 0x829F < =`c`< = 0x82F1.|  
|`_ismbckata`|Katakana znaków dwubajtowych: 0x8340 < =`c`< = 0x8396.|  
|`_ismbckata_l`|Katakana znaków dwubajtowych: 0x8340 < =`c`< = 0x8396.|  
  
 **Strony 932 określonego kodu zakończenia**  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_ismbchira`|\<mbstring.h >|  
|`_ismbchira_l`|\<mbstring.h >|  
|`_ismbckata`|\<mbstring.h >|  
|`_ismbckata_l`|\<mbstring.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasyfikacja znaków](../../c-runtime-library/character-classification.md)   
 [_ismbc — procedury](../../c-runtime-library/ismbc-routines.md)   
 [jest isw — procedury](../../c-runtime-library/is-isw-routines.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)