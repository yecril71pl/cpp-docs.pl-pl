---
title: "tolower, _tolower —, towlower —, _tolower_l —, _towlower_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _tolower_l
- towlower
- tolower
- _tolower
- _towlower_l
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _totlower
- tolower
- _tolower
- towlower
dev_langs: C++
helpviewer_keywords:
- tolower_l function
- _tolower_l function
- totlower function
- string conversion, to different characters
- lowercase, converting to
- tolower function
- string conversion, case
- towlower function
- _tolower function
- _totlower function
- towlower_l function
- case, converting
- characters, converting
- _towlower_l function
ms.assetid: 86e0fc02-94ae-4472-9631-bf8e96f67b92
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bd7c3fd10461033c6b66a96eecd4d5e6ec5941b9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="tolower-tolower-towlower-tolowerl-towlowerl"></a>tolower, _tolower, towlower, _tolower_l, _towlower_l
Konwertuje znak na małe litery.  
  
## <a name="syntax"></a>Składnia  
  
```  
int tolower(  
   int c   
);  
int _tolower(  
   int c   
);  
int towlower(  
   wint_t c   
);  
int _tolower_l(  
   int c,  
   _locale_t locale   
);  
int _towlower_l(  
   wint_t c,  
   _locale_t locale   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`c`  
 Znak do konwersji.  
  
 [in]`locale`  
 Ustawienia regionalne do użycia na potrzeby tłumaczenia specyficzne dla ustawień regionalnych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Każdy z tych procedur konwertuje kopię `c` na małe litery, jeśli konwersja jest możliwa i zwraca wynik. Brak wartości zwracanej jest zastrzeżony wystąpił błąd.  
  
## <a name="remarks"></a>Uwagi  
 Dany wielką literę każdego z tych procedur konwertuje się małą literą, jeśli jest to możliwe i odpowiednie. Wielkość konwersji `towlower` jest specyficzne dla ustawień regionalnych. Tylko znaki dotyczy bieżące ustawienia regionalne są zmieniane w przypadku. Funkcje bez `_l` aktualnie ustawione używać sufiksu ustawień regionalnych. Wersje tych funkcji, które mają `_l` sufiks zająć ustawień regionalnych jako parametr i używać zamiast aktualnie ustawione ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
 Aby `_tolower` do uzyskania oczekiwanych wyników, [__isascii —](../../c-runtime-library/reference/isascii-isascii-iswascii.md) i [isupper —](../../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md) musi zwrócą różną od zera.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_totlower`|`tolower`|`_mbctolower`|`towlower`|  
|`_totlower_l`|`_tolower_l`|`_mbctolower_l`|`_towlower_l`|  
  
> [!NOTE]
>  `_tolower_l`i `_towlower_l` nie zależność od ustawień regionalnych, a nie są przeznaczone do bezpośredniego wywoływania. Są one udostępniane do użytku wewnętrznego przez `_totlower_l`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`tolower`|\<CType.h >|  
|`_tolower`|\<CType.h >|  
|`towlower`|\<CType.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 Zapoznaj się z przykładem w [do funkcji](../../c-runtime-library/to-functions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja danych](../../c-runtime-library/data-conversion.md)   
 [jest isw — procedury](../../c-runtime-library/is-isw-routines.md)   
 [do funkcji](../../c-runtime-library/to-functions.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)