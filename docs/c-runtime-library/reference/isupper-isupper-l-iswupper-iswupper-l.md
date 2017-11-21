---
title: "isupper —, _isupper_l —, iswupper —, _iswupper_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- isupper
- iswupper
- _iswupper_l
- _isupper_l
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
- isupper
- _istupper
- iswupper
dev_langs: C++
helpviewer_keywords:
- istupper function
- iswupper function
- isupper_l function
- _isupper_l function
- iswupper_l function
- _istupper function
- _iswupper_l function
- isupper function
ms.assetid: da2bcc9f-241c-48c0-9a0e-ad273827e16a
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 65ba046c6e2f592dece527f73186220084ca576b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="isupper-isupperl-iswupper-iswupperl"></a>isupper, _isupper_l, iswupper, _iswupper_l
Określa, czy liczba całkowita reprezentuje wielką literę.  
  
## <a name="syntax"></a>Składnia  
  
```  
int isupper(  
   int c   
);  
int _isupper_l (  
   int c,  
   _locale_t locale  
);  
int iswupper(  
   wint_t c   
);  
int _iwsupper_l(  
   wint_t c,  
   _locale_t locale   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `c`  
 Liczba całkowita do testowania.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Każdy z tych procedur zwraca różną od zera, jeśli `c` jest reprezentację określonego obiektu wielką literę. `isupper`Zwraca wartość niezerową, jeśli `c` jest wielką literę (- Z). `iswupper`Zwraca wartość niezerową, jeśli `c` jest znaków dwubajtowych, umożliwiająca wielką literę, lub jeśli `c` jest jednym z zdefiniowane w implementacji zbiór znaki dwubajtowe, dla których żadna z `iswcntrl`, `iswdigit`, `iswpunct`, lub `iswspace` jest różna od zera. Każdy z tych procedur zwraca 0, jeśli `c` nie spełnia warunku.  
  
 Wersje tych funkcji, które mają `_l` sufiks Użyj ustawień regionalnych, który jest przekazywany w zamiast bieżące ustawienia regionalne dla ich działania zależnego od ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
 Zachowanie `isupper` i `_isupper_l` jest niezdefiniowana, jeśli `c` nie jest EOF lub w zakresie od 0 do 0xFF włącznie. Gdy zostanie użyty bibliotek debugowania CRT i `c` nie jest jedną z tych wartości, zgłoś funkcje potwierdzenia.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_istupper`|`isupper`|[_ismbcupper —](../../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|`iswupper`|  
|`_istupper_l`|`_isupper_l`|[_ismbclower —, _ismbclower_l —, _ismbcupper — _ismbcupper_l —](../../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|`_iswupper_l`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`isupper`|\<CType.h >|  
|`_isupper_l`|\<CType.h >|  
|`iswupper`|\<CType.h > lub \<wchar.h >|  
|`_iswupper_l`|\<CType.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasyfikacja znaków](../../c-runtime-library/character-classification.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [jest isw — procedury](../../c-runtime-library/is-isw-routines.md)