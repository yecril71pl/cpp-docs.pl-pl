---
title: _ismbclower, _ismbclower_l, _ismbcupper, _ismbcupper_l
ms.date: 11/04/2016
apiname:
- _ismbclower
- _ismbclower_l
- _ismbcupper_l
- _ismbcupper
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 29a1e97f4583808931e5228a6905aed7c0a62702
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431866"
---
# <a name="ismbclower-ismbclowerl-ismbcupper-ismbcupperl"></a>_ismbclower, _ismbclower_l, _ismbcupper, _ismbcupper_l

Sprawdza, czy znak wielobajtowy jest wielką czy małą literą.

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Znak do zbadania.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każda z tych procedur zwraca wartość różną od zera, jeśli znak spełnia warunek testu lub 0, jeśli nie jest. Jeśli *c*< = 255 i istnieje odpowiedni **_ismbb —** procedura (na przykład **_ismbcalnum —** odpowiada **_ismbbalnum —**), wynik jest wartością zwracaną odpowiadającego **_ismbb —** procedury.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji testuje dany znak wielobajtowy dla danego warunku.

Wersje tych funkcji **_l** sufiksem są identyczne, z tą różnicą, że używają one ustawień regionalnych przekazanych w zamiast bieżących ustawień regionalnych dla swoich zachowań zależnych od ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

|Procedura|Testowanie warunku|Przykład strony kodu 932|
|-------------|--------------------|---------------------------|
|**_ismbclower**|Małe litery alfabetycznie|Zwraca wartość różną od zera wtedy i tylko wtedy, gdy *c* jest reprezentacją jednobajtowego małe litery angielskiej ASCII: 0x61 < =*c*< = 0x7A.|
|**_ismbclower_l**|Małe litery alfabetycznie|Zwraca wartość różną od zera wtedy i tylko wtedy, gdy *c* jest reprezentacją jednobajtowego małe litery angielskiej ASCII: 0x61 < =*c*< = 0x7A.|
|**_ismbcupper —**|Wielkie litery alfabetycznie|Zwraca wartość różną od zera wtedy i tylko wtedy, gdy *c* jest reprezentacją jednobajtowego wielkie litery angielskiej ASCII: 0x41 < =*c*< = 0x5A.|
|**_ismbcupper_l**|Wielkie litery alfabetycznie|Zwraca wartość różną od zera wtedy i tylko wtedy, gdy *c* jest reprezentacją jednobajtowego wielkie litery angielskiej ASCII: 0x41 < =*c*< = 0x5A.|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_ismbclower**|\<mbstring.h>|
|**_ismbclower_l**|\<mbstring.h>|
|**_ismbcupper —**|\<mbstring.h>|
|**_ismbcupper_l**|\<mbstring.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[_ismbc, procedury](../../c-runtime-library/ismbc-routines.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb, procedury](../../c-runtime-library/ismbb-routines.md)<br/>
