---
title: _ismbclower, _ismbclower_l, _ismbcupper, _ismbcupper_l
ms.date: 11/04/2016
api_name:
- _ismbclower
- _ismbclower_l
- _ismbcupper_l
- _ismbcupper
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
- api-ms-win-crt-multibyte-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ismbcupper
- _ismbclower
helpviewer_keywords:
- _ismbcupper function
- ismbclower function
- _ismbclower_l function
- ismbcupper_l function
- _ismbclower function
- ismbcupper function
- ismbclower_l function
- _ismbcupper_l function
ms.assetid: 17d89587-65bc-477c-ba8f-a84e63cf59e7
ms.openlocfilehash: 6a64a0d9be83733fa5482eee84ce6576dd32c221
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953784"
---
# <a name="_ismbclower-_ismbclower_l-_ismbcupper-_ismbcupper_l"></a>_ismbclower, _ismbclower_l, _ismbcupper, _ismbcupper_l

Sprawdza, czy znak wielobajtowy jest pisany małymi lub wielką literą.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _ismbclower(
   unsigned int c
);
int _ismbclower_l(
   unsigned int c,
   _locale_t locale
);
int _ismbcupper(
   unsigned int c
);
int _ismbcupper_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Znak do przetestowania.

*ustawienie*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każda z tych procedur zwraca wartość różną od zera, jeśli znak spełnia warunek testu lub 0, jeśli tak nie jest. Jeśli *c*< = 255 i istnieje odpowiednia procedura **_ismbb** (na przykład **_ismbcalnum** odpowiada **_ismbbalnum**), wynik jest wartością zwracaną odpowiedniej procedury **_ismbb** .

## <a name="remarks"></a>Uwagi

Każda z tych funkcji testuje danego znaku wielobajtowego dla danego warunku.

Wersje tych funkcji z sufiksem **_l** są identyczne, z tą różnicą, że używają ustawień regionalnych przewidzianych zamiast bieżących ustawień regionalnych dla zachowań zależnych od ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

|Procedura|Warunek testu|Przykładowa strona kodowa 932|
|-------------|--------------------|---------------------------|
|**_ismbclower**|Małe litery alfabetu|Zwraca wartość różną od zera, jeśli i tylko wtedy, gdy *c* jest reprezentacją jednobajtowej litery alfabetu angielskiego w formacie ASCII: 0x61 < =*c*< = 0x7a.|
|**_ismbclower_l**|Małe litery alfabetu|Zwraca wartość różną od zera, jeśli i tylko wtedy, gdy *c* jest reprezentacją jednobajtowej litery alfabetu angielskiego w formacie ASCII: 0x61 < =*c*< = 0x7a.|
|**_ismbcupper**|Wielkie litery|Zwraca wartość różną od zera, jeśli i tylko wtedy, gdy *c* jest reprezentacją jednobajtowej wielkiej litery alfabetu ASCII: 0x41 < =*c*< = 0x5a.|
|**_ismbcupper_l**|Wielkie litery|Zwraca wartość różną od zera, jeśli i tylko wtedy, gdy *c* jest reprezentacją jednobajtowej wielkiej litery alfabetu ASCII: 0x41 < =*c*< = 0x5a.|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_ismbclower**|\<mbstring.h>|
|**_ismbclower_l**|\<mbstring.h>|
|**_ismbcupper**|\<mbstring.h>|
|**_ismbcupper_l**|\<mbstring.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[_ismbc, procedury](../../c-runtime-library/ismbc-routines.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb, procedury](../../c-runtime-library/ismbb-routines.md)<br/>
