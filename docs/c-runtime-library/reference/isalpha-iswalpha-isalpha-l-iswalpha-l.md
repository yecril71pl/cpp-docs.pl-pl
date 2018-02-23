---
title: "isalpha —, iswalpha —, _isalpha_l —, _iswalpha_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- iswalpha
- _iswalpha_l
- isalpha
- _isalpha_l
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _istalpha
- _ismbcalpha_l
- isalpha
- _isalpha_l
- iswalpha
- _istalpha_l
- _iswalpha_l
dev_langs:
- C++
helpviewer_keywords:
- _iswalpha_l function
- _isalpha_l function
- _ismbcalpha_l function
- _istalpha_l function
- _ismbcalpha function
- isalpha function
- iswalpha function
- istalpha function
- _istalpha function
ms.assetid: ed6cc2be-c4b0-4475-87ac-bc06d8c23064
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 04f3d1720420ce7b32e9386ccd384de25c78ac79
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="isalpha-iswalpha-isalphal-iswalphal"></a>isalpha, iswalpha, _isalpha_l, _iswalpha_l
Określa, czy liczba całkowita reprezentuje znakiem alfabetycznym.  
  
## <a name="syntax"></a>Składnia  
  
```  
int isalpha(   
   int c   
);  
int iswalpha(   
   wint_t c   
);  
int _isalpha_l(   
   int c,  
   _locale_t locale   
);  
int _iswalpha_l(   
   wint_t c,  
   _locale_t locale   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `c`  
 Liczba całkowita do testowania.  
  
 `locale`  
 Ustawienia regionalne do użycia zamiast bieżących ustawień regionalnych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Każdy z tych procedur zwraca różną od zera, jeśli `c` jest reprezentację określonego obiektu znakiem alfabetycznym. `isalpha` Zwraca wartość niezerową, jeśli `c` jest z zakresu A - Z lub a - z. `iswalpha` Zwraca wartość różną od zera tylko znaki dwubajtowe, dla którego `iswupper` lub `iswlower` jest różna od zera; oznacza to, że dla dowolnego całej znak oznacza to jeden zestaw zdefiniowane w implementacji dla których żaden z `iswcntrl`, `iswdigit`, `iswpunct`, lub `iswspace`jest różna od zera. Każdy z tych procedur zwraca 0, jeśli `c` nie spełnia warunku.  
  
 Wersje tych funkcji, które mają `_l` sufiks Użyj parametr ustawień regionalnych, który jest przekazywany w zamiast bieżących ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
 Zachowanie `isalpha` i `_isalpha_l` jest niezdefiniowana, jeśli `c` nie jest EOF lub w zakresie od 0 do 0xFF włącznie. Gdy zostanie użyty bibliotek debugowania CRT i `c` nie jest jedną z tych wartości, zgłoś funkcje potwierdzenia.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_istalpha`|`isalpha`|`_ismbcalpha`|`iswalpha`|  
|`_istalpha_l`|`_isalpha_l`|`_ismbcalpha_l`|`_iswalpha_l`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`isalpha`|\<ctype.h>|  
|`iswalpha`|\<CType.h > lub \<wchar.h >|  
|`_isalpha_l`|\<ctype.h>|  
|`_iswalpha_l`|\<CType.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasyfikacja znaków](../../c-runtime-library/character-classification.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [is, isw, procedury](../../c-runtime-library/is-isw-routines.md)