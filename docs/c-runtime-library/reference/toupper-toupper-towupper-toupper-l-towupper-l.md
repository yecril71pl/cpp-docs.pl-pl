---
title: toupper, _toupper, towupper, _toupper_l, _towupper_l
ms.date: 11/04/2016
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- towupper
- _toupper
- _totupper
- toupper
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
ms.openlocfilehash: 6dd564a27ee7f3c2bb095564e5c9423249d6babc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155501"
---
# <a name="toupper-toupper-towupper-toupperl-towupperl"></a>toupper, _toupper, towupper, _toupper_l, _towupper_l

Znak przekonwertowania na wielkie litery.

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
Znak do przekształcenia.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każda z tych procedur konwertuje kopię *c*, jeśli jest to możliwe i zwraca wynik.

Jeśli *c* jest znakiem dwubajtowym, dla którego **iswlower —** jest różna od zera i ma odpowiedniego znak dwubajtowy, dla którego [iswupper —](isupper-isupper-l-iswupper-iswupper-l.md) jest różna od zera, **towupper —** zwraca odpowiedni znak dwubajtowy; w przeciwnym razie **towupper —** zwraca *c* bez zmian.

Nie zwraca wartości jest rezerwowana w celu wskazania błędu.

Aby **toupper** do uzyskania oczekiwanych wyników, [__isascii —](isascii-isascii-iswascii.md) i [islower](islower-iswlower-islower-l-iswlower-l.md) musi oba zwracają wartość różną od zera.

## <a name="remarks"></a>Uwagi

Każda z tych procedur konwertuje dany mała litera wielką literą, jeśli jest to możliwe, a odpowiednie. Konwersja przypadków **towupper —** jest specyficzne dla ustawień regionalnych. Tylko znaki, które są istotne dla bieżących ustawień regionalnych zostały zmienione w przypadku. Funkcje bez **_l** sufiksa używa aktualnie ustawione ustawień regionalnych. Wersje tych funkcji **_l** sufiks zająć ustawień regionalnych jako parametru i używać go zamiast aktualnie ustawione ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

Aby **toupper** do uzyskania oczekiwanych wyników, [__isascii —](isascii-isascii-iswascii.md) i [isupper](isupper-isupper-l-iswupper-iswupper-l.md) musi oba zwracają wartość różną od zera.

[Procedury konwersji danych](../../c-runtime-library/data-conversion.md)

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_totupper**|**toupper**|**_mbctoupper**|**towupper —**|
|**_totupper_l**|**_toupper_l**|**_mbctoupper_l**|**_towupper_l —**|

> [!NOTE]
> **_toupper_l —** i **_towupper_l —** ma zależność od nie ustawień regionalnych i nie są przeznaczone do bezpośredniego wywoływania. Są one udostępniane do użytku wewnętrznego przez **_totupper_l**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**toupper**|\<ctype.h>|
|**_toupper**|\<ctype.h>|
|**towupper —**|\<CType.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład w [funkcji](../../c-runtime-library/to-functions.md).

## <a name="see-also"></a>Zobacz także

[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
[to, funkcje](../../c-runtime-library/to-functions.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
