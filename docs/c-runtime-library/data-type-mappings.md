---
title: Mapowanie typu danych
ms.date: 11/04/2016
f1_keywords:
- _TXCHAR
- _TUCHAR
- _TINT
- _TSCHAR
- _TCHAR
- TCHAR::H
- TCHAR
- _T
- _TEXT
helpviewer_keywords:
- _TXCHAR type
- TINT type
- _TCHAR type
- TSCHAR type
- TEXT type
- TCHAR type
- TCHAR.H data types, mappings defined in
- generic-text data types
- _TINT type
- TUCHAR type
- TXCHAR type
- _TSCHAR type
- T type
- _TUCHAR type
- _TEXT type
- _T type
ms.assetid: 4e573c05-8800-468b-ae5f-76ff7409835e
ms.openlocfilehash: 60dc4329ae4c908b9bd168584c71c42c12634bb2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344370"
---
# <a name="data-type-mappings"></a>Mapowanie typu danych

Te mapowania typu danych są definiowane w TCHAR. Godz. i są zależne od tego, czy stałej `_UNICODE` lub `_MBCS` został zdefiniowany w programach.

Aby uzyskać powiązane informacje, zobacz [TCHAR przy użyciu. Typy danych H z kodem _MBCS](../text/using-tchar-h-data-types-with-mbcs-code.md).

### <a name="generic-text-data-type-mappings"></a>Mapowanie typu danych — zwykły tekst

|Zwykły tekst<br /><br /> Nazwa typu danych|SBCS (_UNICODE,<br /><br /> _MBCS nie<br /><br /> definicja)|_MBCS<br /><br /> zdefiniowane|_UNICODE<br /><br /> zdefiniowane|
|--------------------------------------|----------------------------------------------------|------------------------|---------------------------|
|`_TCHAR`|`char`|`char`|`wchar_t`|
|`_tfinddata_t`|`_finddata_t`|`_finddata_t`|`_wfinddata_t`|
|`_tfinddata64_t`|`__finddata64_t`|`__finddata64_t`|`__wfinddata64_t`|
|`_tfinddatai64_t`|`_finddatai64_t`|`_finddatai64_t`|`_wfinddatai64_t`|
|`_TINT`|`int`|`int`|`wint_t`|
|`_TSCHAR`|`signed char`|`signed char`|`wchar_t`|
|`_TUCHAR`|`unsigned char`|`unsigned char`|`wchar_t`|
|`_TXCHAR`|`char`|`unsigned char`|`wchar_t`|
|`_T` lub `_TEXT`|Żadnego skutku (usuwane przez preprocesor)|Żadnego skutku (usuwane przez preprocesor)|`L` (konwertuje zgodnie z jego odpowiednikiem Unicode znak lub ciąg)|

## <a name="see-also"></a>Zobacz także

[Mapowania zwykłego tekstu](../c-runtime-library/generic-text-mappings.md)<br/>
[Mapowania zmiennych globalnych i stałych](../c-runtime-library/constant-and-global-variable-mappings.md)<br/>
[Mapowania procedur](../c-runtime-library/routine-mappings.md)<br/>
[Przykładowy ogólny program tekstowy](../c-runtime-library/a-sample-generic-text-program.md)<br/>
[Mapowania zwykłego tekstu](../c-runtime-library/using-generic-text-mappings.md)
