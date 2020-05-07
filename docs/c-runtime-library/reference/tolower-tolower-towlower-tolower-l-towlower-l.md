---
title: tolower, _tolower, towlower, _tolower_l, _towlower_l
ms.date: 4/2/2020
api_name:
- _tolower_l
- towlower
- tolower
- _tolower
- _towlower_l
- _o__tolower
- _o__tolower_l
- _o__towlower_l
- _o_tolower
- _o_towlower
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _totlower
- tolower
- _tolower
- towlower
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
ms.openlocfilehash: c8b27c4cc618d34d9da9b5884c6db2f525fd2388
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910009"
---
# <a name="tolower-_tolower-towlower-_tolower_l-_towlower_l"></a>tolower, _tolower, towlower, _tolower_l, _towlower_l

Konwertuje znak na małe litery.

## <a name="syntax"></a>Składnia

```C
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

### <a name="parameters"></a>Parametry

*s*<br/>
Znak do przekonwertowania.

*locale*<br/>
Ustawienia regionalne do użycia dla tłumaczenia specyficznego dla ustawień regionalnych.

## <a name="return-value"></a>Wartość zwracana

Każda z tych procedur konwertuje kopię *c* na małe litery, jeśli konwersja jest możliwa i zwraca wynik. Brak wartości zwracanej zastrzeżonej do wskazania błędu.

## <a name="remarks"></a>Uwagi

Każda z tych procedur konwertuje daną wielką literę na małą literę, jeśli jest to możliwe i istotne. Konwersja przypadku **towlower** jest specyficzna dla ustawień regionalnych. W przypadku zmiany tylko znaków istotnych dla bieżących ustawień regionalnych. Funkcje bez sufiksu **_l** używają obecnie ustawionych ustawień regionalnych. Wersje tych funkcji, które mają sufiks **_l** przyjmują ustawienia regionalne jako parametr i używają go zamiast obecnie ustawionych ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Aby **_tolower** zapewnić oczekiwane wyniki, [__isascii](isascii-isascii-iswascii.md) i [IsUpper](isupper-isupper-l-iswupper-iswupper-l.md) muszą zwracać wartość różną od zera.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_totlower**|**ToLower**|**_mbctolower**|**towlower**|
|**_totlower_l**|**_tolower_l**|**_mbctolower_l**|**_towlower_l**|

> [!NOTE]
> **_tolower_l** i **_towlower_l** nie są zależne od ustawień regionalnych i nie są przeznaczone do bezpośredniego wywoływania. Są one przeznaczone do użytku wewnętrznego przez **_totlower_l**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**ToLower**|\<CType. h>|
|**_tolower**|\<CType. h>|
|**towlower**|\<CType. h> lub \<WCHAR. h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zapoznaj się z przykładem w [funkcji](../../c-runtime-library/to-functions.md).

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
[do funkcji](../../c-runtime-library/to-functions.md)<br/>
[Ustawienie](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
