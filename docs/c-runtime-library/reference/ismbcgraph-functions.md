---
title: _ismbcgraph, _ismbcgraph_l, _ismbcprint, _ismbcprint_l, _ismbcpunct, _ismbcpunct_l, _ismbcblank, _ismbcblank_l, _ismbcspace, _ismbcspace_l
ms.date: 4/2/2020
api_name:
- _ismbcpunct_l
- _ismbcblank
- _ismbcprint
- _ismbcgraph_l
- _ismbcblank_l
- _ismbcpunct
- _ismbcprint_l
- _ismbcspace_l
- _ismbcspace
- _ismbcgraph
- _o__ismbcblank
- _o__ismbcblank_l
- _o__ismbcgraph
- _o__ismbcgraph_l
- _o__ismbcprint
- _o__ismbcprint_l
- _o__ismbcpunct
- _o__ismbcpunct_l
- _o__ismbcspace
- _o__ismbcspace_l
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ismbcspace
- _ismbcgraph
- _ismbcpunct
- ismbcspace_l
- ismbcgraph
- _ismbcgraph_l
- _ismbcprint
- _ismbcspace_l
- ismbcprint
- ismbcgraph_l
- ismbcspace
- ismbcpunct
helpviewer_keywords:
- ismbcspace_l function
- _ismbcprint_l function
- ismbcspace function
- ismbcpunct function
- _ismbcspace_l function
- _ismbcprint function
- ismbcprint function
- _ismbcgraph function
- ismbcgraph_l function
- _ismbcpunct_l function
- ismbcpunct_l function
- ismbcprint_l function
- _ismbcpunct function
- ismbcgraph function
- _ismbcgraph_l function
- _ismbcspace function
ms.assetid: 8e0a5f47-ba64-4411-92a3-3c525d16e3be
ms.openlocfilehash: 5f2c8b595de323994aa670a8e0fee9e562897e49
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919760"
---
# <a name="_ismbcgraph-_ismbcgraph_l-_ismbcprint-_ismbcprint_l-_ismbcpunct-_ismbcpunct_l-_ismbcblank-_ismbcblank_l-_ismbcspace-_ismbcspace_l"></a>_ismbcgraph, _ismbcgraph_l, _ismbcprint, _ismbcprint_l, _ismbcpunct, _ismbcpunct_l, _ismbcblank, _ismbcblank_l, _ismbcspace, _ismbcspace_l

Określa, czy znak jest znakiem graficznym, znakiem wyświetlanym, znakiem interpunkcyjny lub znakiem spacji.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _ismbcgraph(
   unsigned int c
);
int _ismbcgraph_l(
   unsigned int c,
   _locale_t locale
);
int _ismbcprint(
   unsigned int c
);
int _ismbcprint_l(
   unsigned int c,
   _locale_t locale
);
int _ismbcpunct(
   unsigned int c
);
int _ismbcpunct_l(
   unsigned int c,
   _locale_t locale
);
int _ismbcblank(
   unsigned int c
);
int _ismbcblank_l(
   unsigned int c,
   _locale_t locale
);
int _ismbcspace(
   unsigned int c
);
int _ismbcspace_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*s*<br/>
Znak, który ma zostać określony.

*locale*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każda z tych procedur zwraca wartość różną od zera, jeśli znak spełnia warunek testu lub 0, jeśli tak nie jest. Jeśli *c* <= 255 i istnieje odpowiadająca procedura **_ismbb** (na przykład **_ismbcalnum** odnosi się do **_ismbbalnum**), wynik jest wartością zwracaną odpowiedniej procedury **_ismbb** .

Wersje tych funkcji są identyczne, z tą różnicą, że te, które mają sufiks **_l** używają ustawień regionalnych, które są przenoszone dla zachowań zależnych od ustawień regionalnych, zamiast bieżących ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

## <a name="remarks"></a>Uwagi

Każda z tych funkcji testuje danego znaku wielobajtowego dla danego warunku.

|Procedura|Warunek testu|Przykładowa strona kodowa 932|
|-------------|--------------------|---------------------------|
|**_ismbcgraph**|Zdjęć|Zwraca wartość różną od zera, jeśli i tylko wtedy, gdy *c* jest jednobajtową reprezentacją dowolnego znaku ASCII lub Katakana drukowalnego, z wyjątkiem odstępu ().|
|**_ismbcprint**|Drukowalnych|Zwraca wartość różną od zera, jeśli i tylko wtedy, gdy *c* jest jednobajtową reprezentacją dowolnego znaku ASCII lub Katakana drukowalnego, w tym odstępu ().|
|**_ismbcpunct**|Znaki interpunkcyjne|Zwraca wartość różną od zera, jeśli i tylko wtedy, gdy *c* jest reprezentacją jednobajtowego znaku interpunkcyjny ASCII lub Katakana.|
|**_ismbcblank**|Spacja lub tabulator poziomy|Zwraca wartość różną od zera, jeśli i tylko wtedy, gdy *c* jest spacją lub tabulatorem poziomym: *c*= 0x20 lub *c*= 0x09.|
|**_ismbcspace**|Biały znak|Zwraca wartość różną od zera, jeśli i tylko wtedy, gdy *c* jest znakiem odstępu: *c*= 0x20 lub 0x09<=*c*<= 0x0D.|

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_ismbcgraph**|\<mbstring. h>|
|**_ismbcgraph_l**|\<mbstring. h>|
|**_ismbcprint**|\<mbstring. h>|
|**_ismbcprint_l**|\<mbstring. h>|
|**_ismbcpunct**|\<mbstring. h>|
|**_ismbcpunct_l**|\<mbstring. h>|
|**_ismbcblank**|\<mbstring. h>|
|**_ismbcblank_l**|\<mbstring. h>|
|**_ismbcspace**|\<mbstring. h>|
|**_ismbcspace_l**|\<mbstring. h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz też

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[Ustawienie](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Procedury _ismbc](../../c-runtime-library/ismbc-routines.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb, procedury](../../c-runtime-library/ismbb-routines.md)<br/>
