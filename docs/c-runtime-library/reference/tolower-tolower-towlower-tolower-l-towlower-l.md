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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 560fde4ae2167256acd54856fced15bc6ccecae6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362360"
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

*C*<br/>
Znak do konwersji.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia w przypadku tłumaczenia specyficznego dla ustawień regionalnych.

## <a name="return-value"></a>Wartość zwracana

Każda z tych procedur konwertuje kopię *c* na małe litery, jeśli konwersja jest możliwa, i zwraca wynik. Nie ma wartości zwracanej zarezerwowanej w celu wskazania błędu.

## <a name="remarks"></a>Uwagi

Każda z tych procedur konwertuje daną wielką literę na wielką literę, jeśli jest to możliwe i istotne. Konwersja przypadku **towlower** jest specyficzne dla ustawień regionalnych. W przypadku zmiany są zmieniane tylko znaki istotne dla bieżących ustawień regionalnych. Funkcje bez sufiksu **_l** używają aktualnie ustawionych ustawień regionalnych. Wersje tych funkcji, które mają sufiks **_l,** przyjmują ustawienia regionalne jako parametr i używają tego zamiast aktualnie ustawionych ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Aby **_tolower** dał oczekiwane wyniki, [__isascii](isascii-isascii-iswascii.md) i [isupper](isupper-isupper-l-iswupper-iswupper-l.md) muszą zarówno powrócić nonzero.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_totlower**|**Tolower**|**_mbctolower**|**holownik**|
|**_totlower_l**|**_tolower_l**|**_mbctolower_l**|**_towlower_l**|

> [!NOTE]
> **_tolower_l** i **_towlower_l** nie mają zależności od lokalizacji i nie mają być wywoływane bezpośrednio. Są one przeznaczone do użytku wewnętrznego przez **_totlower_l**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**Tolower**|\<ctype.h>|
|**_tolower**|\<ctype.h>|
|**holownik**|\<ctype.h> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład w [funkcji](../../c-runtime-library/to-functions.md).

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
[do funkcji](../../c-runtime-library/to-functions.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
