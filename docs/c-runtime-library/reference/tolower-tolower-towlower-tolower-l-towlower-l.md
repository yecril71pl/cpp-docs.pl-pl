---
title: tolower, _tolower —, towlower —, _tolower_l —, _towlower_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 49b52bd65439165ef8dd83917a0d75926caba518
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023669"
---
# <a name="tolower-tolower-towlower-tolowerl-towlowerl"></a>tolower, _tolower, towlower, _tolower_l, _towlower_l

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

*c*<br/>
Znak do przekształcenia.

*Ustawienia regionalne*<br/>
Ustawienia regionalne na potrzeby tłumaczenia specyficzne dla ustawień regionalnych.

## <a name="return-value"></a>Wartość zwracana

Każda z tych procedur konwertuje kopię *c* na małe litery, jeśli konwersja jest możliwa i zwraca wynik. Nie zwraca wartości jest rezerwowana w celu wskazania błędu.

## <a name="remarks"></a>Uwagi

Każda z tych procedur konwertuje dany wielką literą małej literze, jeśli jest możliwe odpowiednie. Konwersja przypadków **towlower —** jest specyficzne dla ustawień regionalnych. Tylko znaki, które są istotne dla bieżących ustawień regionalnych zostały zmienione w przypadku. Funkcje bez **_l** sufiksa używa aktualnie ustawione ustawień regionalnych. Wersje tych funkcji, które mają **_l** sufiks zająć ustawień regionalnych jako parametru i używać go zamiast aktualnie ustawione ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

Aby **_tolower —** do uzyskania oczekiwanych wyników, [__isascii —](isascii-isascii-iswascii.md) i [isupper](isupper-isupper-l-iswupper-iswupper-l.md) musi oba zwracają wartość różną od zera.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_totlower —**|**tolower**|**_mbctolower**|**towlower**|
|**_totlower_l**|**_tolower_l**|**_mbctolower_l**|**_towlower_l**|

> [!NOTE]
> **_tolower_l —** i **_towlower_l —** ma zależność od nie ustawień regionalnych i nie są przeznaczone do bezpośredniego wywoływania. Są one udostępniane do użytku wewnętrznego przez **_totlower_l**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**tolower**|\<ctype.h>|
|**_tolower**|\<ctype.h>|
|**towlower**|\<CType.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład w [funkcji](../../c-runtime-library/to-functions.md).

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
[to, funkcje](../../c-runtime-library/to-functions.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
