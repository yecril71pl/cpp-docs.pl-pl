---
title: "toupper, _toupper —, towupper —, _toupper_l —, _towupper_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _toupper_l
- towupper
- toupper
- _towupper_l
- _toupper
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
- towupper
- _toupper
- _totupper
- toupper
dev_langs: C++
helpviewer_keywords:
- _toupper function
- towupper function
- uppercase, converting strings to
- totupper function
- string conversion, to different characters
- towupper_l function
- toupper_l function
- string conversion, case
- _toupper_l function
- _towupper_l function
- _totupper function
- case, converting
- characters, converting
- toupper function
ms.assetid: cdef1b0f-b19c-4d11-b7d2-cf6334c9b6cc
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a40472922e61cbcc6c5788d575305613ae300e1e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="toupper-toupper-towupper-toupperl-towupperl"></a>toupper, _toupper, towupper, _toupper_l, _towupper_l
Konwertuj znaki na wielkie litery.  
  
## <a name="syntax"></a>Składnia  
  
```  
int toupper(  
   int c   
);  
int _toupper(  
   int c   
);  
int towupper(  
   wint_t c   
);  
int _toupper_l(  
   int c ,  
   _locale_t locale  
);  
int _towupper_l(  
   wint_t c ,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `c`  
 Znak do konwersji.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Każdy z tych procedur konwertuje kopię `c`, jeśli to możliwe i zwraca wynik.  
  
 Jeśli `c` jest znaków dwubajtowych, dla którego `iswlower` jest różna od zera i ma odpowiedniego znaków dwubajtowych, dla którego `iswupper` jest różna od zera, `towupper` zwraca odpowiednie szerokość znaku; w przeciwnym razie `towupper` zwraca `c`bez zmian.  
  
 Brak wartości zwracanej jest zastrzeżony wystąpił błąd.  
  
 Aby `toupper` do uzyskania oczekiwanych wyników, [__isascii —](../../c-runtime-library/reference/isascii-isascii-iswascii.md) i [islower —](../../c-runtime-library/reference/islower-iswlower-islower-l-iswlower-l.md) musi zwrócą różną od zera.  
  
## <a name="remarks"></a>Uwagi  
 Każdy z tych procedur konwertuje danego małej litery na wielką literę, jeśli to możliwe i odpowiednią. Wielkość konwersji `towupper` jest specyficzne dla ustawień regionalnych. Tylko znaki dotyczy bieżące ustawienia regionalne są zmieniane w przypadku. Funkcje bez `_l` aktualnie ustawione używać sufiksu ustawień regionalnych. Wersje tych funkcji z `_l` sufiks zająć ustawień regionalnych jako parametr i używać zamiast aktualnie ustawione ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
 Aby `toupper` do uzyskania oczekiwanych wyników, [__isascii —](../../c-runtime-library/reference/isascii-isascii-iswascii.md) i [isupper —](../../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md) musi zwrócą różną od zera.  
  
 [Procedury konwersji danych](../../c-runtime-library/data-conversion.md)  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_totupper`|`toupper`|`_mbctoupper`|`towupper`|  
|`_totupper_l`|`_toupper_l`|`_mbctoupper_l`|`_towupper_l`|  
  
> [!NOTE]
>  `_toupper_l`i `_towupper_l` nie zależność od ustawień regionalnych, a nie są przeznaczone do bezpośredniego wywoływania. Są one udostępniane do użytku wewnętrznego przez `_totupper_l`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`toupper`|\<CType.h >|  
|`_toupper`|\<CType.h >|  
|`towupper`|\<CType.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 Zapoznaj się z przykładem w [do funkcji](../../c-runtime-library/to-functions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [jest isw — procedury](../../c-runtime-library/is-isw-routines.md)   
 [do funkcji](../../c-runtime-library/to-functions.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)