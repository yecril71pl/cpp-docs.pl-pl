---
title: toupper, _toupper, towupper, _toupper_l, _towupper_l
ms.date: 4/2/2020
api_name:
- _toupper_l
- towupper
- toupper
- _towupper_l
- _toupper
- _o__toupper
- _o__toupper_l
- _o__towupper_l
- _o_toupper
- _o_towupper
api_location:
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 85c218fdb3f5153e572e434bffbdb64510554d07
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362323"
---
# <a name="toupper-_toupper-towupper-_toupper_l-_towupper_l"></a>toupper, _toupper, towupper, _toupper_l, _towupper_l

Konwertuj znak na wielkie litery.

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

*C*<br/>
Znak do konwersji.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każda z tych procedur konwertuje kopię *c*, jeśli to możliwe, i zwraca wynik.

Jeśli *c* jest znakiem szerokim, dla którego **iswlower** jest niezerowy i istnieje odpowiedni szeroki znak, dla którego [iswupper](isupper-isupper-l-iswupper-iswupper-l.md) jest różny od zera, **towupper** zwraca odpowiedni szeroki znak; w przeciwnym razie **towupper** zwraca *c* bez zmian.

Nie ma wartości zwracanej zarezerwowanej w celu wskazania błędu.

Aby **toupper** dać oczekiwane wyniki, [__isascii](isascii-isascii-iswascii.md) i [wolniej](islower-iswlower-islower-l-iswlower-l.md) musi zarówno powrót nonzero.

## <a name="remarks"></a>Uwagi

W każdym z tych procedur można przekonwertować daną wielką literę na wielką literę, jeśli to możliwe i jest to konieczne. Konwersja przypadku **towupper** jest specyficzne dla ustawień regionalnych. W przypadku zmiany są zmieniane tylko znaki istotne dla bieżących ustawień regionalnych. Funkcje bez sufiksu **_l** używają aktualnie ustawionych ustawień regionalnych. Wersje tych funkcji z sufiksem **_l** przyjmują ustawienia regionalne jako parametr i używają tego zamiast aktualnie ustawionych ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Aby **toupper** dać oczekiwane wyniki, [__isascii](isascii-isascii-iswascii.md) i [isupper](isupper-isupper-l-iswupper-iswupper-l.md) musi zarówno powrót nonzero.

[Procedury konwersji danych](../../c-runtime-library/data-conversion.md)

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_totupper**|**Toupper**|**_mbctoupper**|**holowniczy**|
|**_totupper_l**|**_toupper_l**|**_mbctoupper_l**|**_towupper_l**|

> [!NOTE]
> **_toupper_l** i **_towupper_l** nie mają zależności od lokalizacji i nie mają być wywoływane bezpośrednio. Są one przeznaczone do użytku wewnętrznego przez **_totupper_l**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**Toupper**|\<ctype.h>|
|**_toupper**|\<ctype.h>|
|**holowniczy**|\<ctype.h> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład w [funkcji](../../c-runtime-library/to-functions.md).

## <a name="see-also"></a>Zobacz też

[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
[do funkcji](../../c-runtime-library/to-functions.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
