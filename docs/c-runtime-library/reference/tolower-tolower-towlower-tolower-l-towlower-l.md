---
title: tolower, _tolower —, towlower —, _tolower_l —, _towlower_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- _totlower
- tolower
- _tolower
- towlower
dev_langs:
- C++
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
caps.latest.revision: ''
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 44c75ab979db21d72c682a3ba6f0da6947f22a4c
ms.sourcegitcommit: 604907f77eb6c5b1899194a9877726f3e8c2dabc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
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
 [in] `c`  
 Znak do konwersji.  
  
 [in] `locale`  
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
>  `_tolower_l` i `_towlower_l` nie zależność od ustawień regionalnych, a nie są przeznaczone do bezpośredniego wywoływania. Są one udostępniane do użytku wewnętrznego przez `_totlower_l`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`tolower`|\<ctype.h>|  
|`_tolower`|\<ctype.h>|  
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