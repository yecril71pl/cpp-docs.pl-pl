---
title: toupper, _toupper —, towupper —, _toupper_l —, _towupper_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 73157691cc1635d038339d9fe707aa535e1df93f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32413463"
---
# <a name="toupper-toupper-towupper-toupperl-towupperl"></a>toupper, _toupper, towupper, _toupper_l, _towupper_l

Konwertuj znaki na wielkie litery.

## <a name="syntax"></a>Składnia

```C
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

### <a name="parameters"></a>Parametry

*c*<br/>
Znak do konwersji.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każdy z tych procedur konwertuje kopię *c*, jeśli to możliwe i zwraca wynik.

Jeśli *c* jest znaków dwubajtowych, dla którego **iswlower —** jest różna od zera i ma odpowiedniego znaków dwubajtowych, dla którego [iswupper —](isupper-isupper-l-iswupper-iswupper-l.md) jest różna od zera, **towupper —** zwraca odpowiedniego znaków dwubajtowych; w przeciwnym razie **towupper —** zwraca *c* bez zmian.

Brak wartości zwracanej jest zastrzeżony wystąpił błąd.

Aby **toupper** do uzyskania oczekiwanych wyników, [__isascii —](isascii-isascii-iswascii.md) i [islower —](islower-iswlower-islower-l-iswlower-l.md) musi zwrócą różną od zera.

## <a name="remarks"></a>Uwagi

Każdy z tych procedur konwertuje danego małej litery na wielką literę, jeśli to możliwe i odpowiednią. Wielkość konwersji **towupper —** jest specyficzne dla ustawień regionalnych. Tylko znaki dotyczy bieżące ustawienia regionalne są zmieniane w przypadku. Funkcje bez **_l** aktualnie ustawione używać sufiksu ustawień regionalnych. Wersje tych funkcji z **_l** sufiks zająć ustawień regionalnych jako parametr i używać zamiast aktualnie ustawione ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

Aby **toupper** do uzyskania oczekiwanych wyników, [__isascii —](isascii-isascii-iswascii.md) i [isupper —](isupper-isupper-l-iswupper-iswupper-l.md) musi zwrócą różną od zera.

[Procedury konwersji danych](../../c-runtime-library/data-conversion.md)

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_totupper —**|**toupper**|**_mbctoupper —**|**towupper —**|
|**_totupper_l**|**_toupper_l —**|**_mbctoupper_l —**|**_towupper_l —**|

> [!NOTE]
> **_toupper_l —** i **_towupper_l —** nie zależność od ustawień regionalnych, a nie są przeznaczone do bezpośredniego wywoływania. Są one udostępniane do użytku wewnętrznego przez **_totupper_l**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**toupper**|\<ctype.h>|
|**_toupper —**|\<ctype.h>|
|**towupper —**|\<CType.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zapoznaj się z przykładem w [do funkcji](../../c-runtime-library/to-functions.md).

## <a name="see-also"></a>Zobacz także

[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
[to, funkcje](../../c-runtime-library/to-functions.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
