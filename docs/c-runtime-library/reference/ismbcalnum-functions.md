---
title: _ismbcalnum, _ismbcalnum_l, _ismbcalpha, _ismbcalpha_l, _ismbcdigit, _ismbcdigit_l
ms.date: 11/04/2016
apiname:
- _ismbcalpha
- _ismbcalnum
- _ismbcdigit
- _ismbcalnum_l
- _ismbcdigit_l
- _ismbcalpha_l
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
- _ismbcdigit
- ismbcalnum_l
- _ismbcdigit_l
- _ismbcalpha
- ismbcalnum
- ismbcdigit
- ismbcalpha
- _ismbcalnum_l
- _ismbcalnum
- ismbcdigit_l
helpviewer_keywords:
- ismbcalpha function
- _ismbcalnum function
- ismbcdigit_l function
- _ismbcalnum_l function
- _ismbcdigit function
- ismbcalnum function
- _ismbcalpha_l function
- ismbcdigit function
- _ismbcalpha function
- _ismbcdigit_l function
- ismbcalnum_l function
- ismbcalpha_l function
ms.assetid: 12d57925-aebe-46e0-80b0-82b84c4c31ec
ms.openlocfilehash: 1a2f928d826b70b788220130f69c53cc351b4910
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157311"
---
# <a name="ismbcalnum-ismbcalnuml-ismbcalpha-ismbcalphal-ismbcdigit-ismbcdigitl"></a>_ismbcalnum, _ismbcalnum_l, _ismbcalpha, _ismbcalpha_l, _ismbcdigit, _ismbcdigit_l

Sprawdza, czy znak wielobajtowy jest znakiem alfanumerycznym, alfabetycznym czy znak cyfry.

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _ismbcalnum
(
   unsigned int c
);
int _ismbcalnum_l
(
   unsigned int c,
   _locale_t locale
);
int _ismbcalpha
(
   unsigned int c
);
int _ismbcalpha_l
(
   unsigned int c,
   _locale_t locale
);
int _ismbcdigit
(
   unsigned int c
);
int _ismbcdigit_l
(
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

Każda z tych procedur testuje dany znak wielobajtowy dla danego warunku.

Wersje tych funkcji **_l** sufiksem są identyczne, z tą różnicą, że używają one ustawień regionalnych przekazanych w zamiast bieżących ustawień regionalnych dla swoich zachowań zależnych od ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

|Procedura|Testowanie warunku|Przykład strony kodu 932|
|-------------|--------------------|---------------------------|
|**_ismbcalnum —**, **_ismbcalnum_l —**|Alfanumeryczne|Zwraca wartość różną od zera wtedy i tylko wtedy, gdy *c* jest reprezentacją jednobajtowego jednobajtową litery angielskiej ASCII: Zobacz przykłady dla **_ismbcdigit —** i **_ismbcalpha —**.|
|**_ismbcalpha —**, **_ismbcalpha_l —**|Alfabetyczne|Zwraca wartość różną od zera wtedy i tylko wtedy, gdy *c* jest reprezentacją jednobajtowego jednobajtową litery angielskiej ASCII: 0x41 < =*c*< = 0x5A lub 0x61 < =*c*< = 0x7A; lub literę katakana: 0xA6<=*c*<=0xDF.|
|**_ismbcdigit —**, **_ismbcdigit —**|cyfra|Zwraca wartość różną od zera wtedy i tylko wtedy, gdy *c* jest reprezentacją jednobajtowego cyfr ASCII: 0x30 < =*c*< = 0x39.|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_ismbcalnum —**, **_ismbcalnum_l —**|\<mbstring.h>|
|**_ismbcalpha —**, **_ismbcalpha_l —**|\<mbstring.h>|
|**_ismbcdigit**, **_ismbcdigit_l**|\<mbstring.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[_ismbc, procedury](../../c-runtime-library/ismbc-routines.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb, procedury](../../c-runtime-library/ismbb-routines.md)<br/>
