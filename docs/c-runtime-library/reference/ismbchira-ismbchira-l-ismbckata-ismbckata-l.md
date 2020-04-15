---
title: _ismbchira, _ismbchira_l, _ismbckata, _ismbckata_l
ms.date: 4/2/2020
api_name:
- _ismbckata
- _ismbchira_l
- _ismbchira
- _ismbckata_l
- _o__ismbchira
- _o__ismbchira_l
- _o__ismbckata
- _o__ismbckata_l
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ismbckata_l
- _ismbckata_l
- ismbckata
- ismbchira
- _ismbckata
- ismbchira_l
- _ismbchira_l
- _ismbchira
helpviewer_keywords:
- _ismbckata function
- _ismbchira function
- _ismbckata_l function
- Katakana
- ismbchira function
- _ismbchira_l function
- ismbchira_l function
- ismbdkata_l function
- Hiragana
- ismbckata function
ms.assetid: 2db388a2-be31-489b-81c8-f6bf3f0582d3
ms.openlocfilehash: d450702ae41f404606cda1bea613f3d99fadd06f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343216"
---
# <a name="_ismbchira-_ismbchira_l-_ismbckata-_ismbckata_l"></a>_ismbchira, _ismbchira_l, _ismbckata, _ismbckata_l

**Strona kodowa 932 Określone funkcje**

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _ismbchira(
   unsigned int c
);
int _ismbchira_l(
   unsigned int c,
   _locale_t locale
);
int _ismbckata(
   unsigned int c
);
int _ismbckata_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*C*<br/>
Znak do przetestowania.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każda z tych procedur zwraca wartość niezerową, jeśli znak spełnia warunek testu lub 0, jeśli nie. Jeśli *c* <= 255 i istnieje **odpowiednia _ismbb** rutynowa (na przykład **_ismbcalnum** odpowiada **_ismbbalnum),** wynikiem jest wartość zwracana odpowiedniej **_ismbb** rutynowej.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji testuje dany znak wielobajtowy dla danego warunku.

Wersje tych funkcji z sufiksem **_l** są identyczne, z tą różnicą, że używają ustawień regionalnych przekazanych zamiast bieżących ustawień regionalnych dla ich zachowania zależnego od ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

|Procedura|Warunek testu (tylko strona kodowa 932)|
|-------------|-------------------------------------------|
|**_ismbchira**|Hiragana dwu bajtowa: 0x829F<=*c*<=0x82F1.|
|**_ismbchira_l**|Hiragana dwu bajtowa: 0x829F<=*c*<=0x82F1.|
|**_ismbckata**|Katakana dwu bajtowa: 0x8340<=*c*<=0x8396.|
|**_ismbckata_l**|Katakana dwu bajtowa: 0x8340<=*c*<=0x8396.|

**Koniec strony kodowej 932 Specyficzne**

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_ismbchira**|\<mbstring.h>|
|**_ismbchira_l**|\<mbstring.h>|
|**_ismbckata**|\<mbstring.h>|
|**_ismbckata_l**|\<mbstring.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[Procedury _ismbc](../../c-runtime-library/ismbc-routines.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
