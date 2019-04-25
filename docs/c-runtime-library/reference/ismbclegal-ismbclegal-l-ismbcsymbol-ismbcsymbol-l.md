---
title: _ismbclegal, _ismbclegal_l, _ismbcsymbol, _ismbcsymbol_l
ms.date: 11/04/2016
apiname:
- _ismbclegal_l
- _ismbclegal
- _ismbcsymbol
- _ismbcsymbol_l
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
- ismbcsymbol_l
- _ismbcsymbol_l
- _ismbcsymbol
- _ismbclegal_l
- _ismbclegal
- ismbclegal_l
- ismbcsymbol
- ismbclegal
helpviewer_keywords:
- ismbcsymbol function
- ismbclegal_l function
- _istlegal_l function
- istlegal function
- _istlegal function
- _ismbcsymbol function
- _ismbclegal_l function
- ismbclegal function
- ismbcsymbol_l function
- _ismbclegal function
- _ismbcsymbol_l function
- istlegal_l function
ms.assetid: 31bf1ea5-b56f-4e28-b21e-b49a2cf93ffc
ms.openlocfilehash: 07855ec970b2bf307238982987912f1e91505e96
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62286835"
---
# <a name="ismbclegal-ismbclegall-ismbcsymbol-ismbcsymboll"></a>_ismbclegal, _ismbclegal_l, _ismbcsymbol, _ismbcsymbol_l

Sprawdza, czy znak wielobajtowy jest prawnym czy symbolem znaków.

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _ismbclegal(
   unsigned int c
);
int _ismbclegal_l(
   unsigned int c,
   _locale_t locale
);
int _ismbcsymbol(
   unsigned int c
);
int _ismbcsymbol_l(
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
|**_ismbclegal**|Prawidłowe wielobajtowe|Zwraca wartość różną od zera wtedy i tylko wtedy, gdy pierwszy bajt *c* znajduje się w zakresach 0x81-0x9F lub wartość 0xE0 — 0xFC, podczas gdy drugi bajt jest w zakresach 0x40-0x7E lub 0x80 - FC.|
|**_ismbcsymbol**|Symbol wielobajtowy|Zwraca wartość różną od zera wtedy i tylko wtedy, gdy 0x8141 < =*c*< = 0x81AC.|

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istlegal**|Zawsze zwraca wartość false|**_ismbclegal**|zawsze zwraca wartość false.|
|**_istlegal_l**|Zawsze zwraca wartość false|**_ismbclegal_l**|zawsze zwraca wartość false.|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_ismbclegal —**, **_ismbclegal_l —**|\<mbstring.h>|
|**_ismbcsymbol**, **_ismbcsymbol_l**|\<mbstring.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[_ismbc, procedury](../../c-runtime-library/ismbc-routines.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb, procedury](../../c-runtime-library/ismbb-routines.md)<br/>
