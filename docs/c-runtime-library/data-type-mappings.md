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
ms.openlocfilehash: d77ac4fa9afcd5a6b8f86261c7a3ba466adc64a4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215156"
---
# <a name="data-type-mappings"></a>Mapowanie typu danych

Te mapowania typu danych są zdefiniowane w używanie TCHAR. H i zależy od tego, czy stała `_UNICODE` lub `_MBCS` została zdefiniowana w programie.

Aby uzyskać powiązane informacje, zobacz [using używanie TCHAR. H typy danych z kodem _MBCS](../text/using-tchar-h-data-types-with-mbcs-code.md).

### <a name="generic-text-data-type-mappings"></a>Mapowanie typu danych tekstu ogólnego

|Tekst ogólny<br /><br /> Nazwa typu danych|SBCS (_UNICODE,<br /><br /> Nie _MBCS<br /><br /> określonych|_MBCS<br /><br /> zdefiniowane|_UNICODE<br /><br /> zdefiniowane|
|--------------------------------------|----------------------------------------------------|------------------------|---------------------------|
|`_TCHAR`|**`char`**|**`char`**|**`wchar_t`**|
|`_tfinddata_t`|`_finddata_t`|`_finddata_t`|`_wfinddata_t`|
|`_tfinddata64_t`|`__finddata64_t`|`__finddata64_t`|`__wfinddata64_t`|
|`_tfinddatai64_t`|`_finddatai64_t`|`_finddatai64_t`|`_wfinddatai64_t`|
|`_TINT`|**`int`**|**`int`**|`wint_t`|
|`_TSCHAR`|**`signed char`**|**`signed char`**|**`wchar_t`**|
|`_TUCHAR`|**`unsigned char`**|**`unsigned char`**|**`wchar_t`**|
|`_TXCHAR`|**`char`**|**`unsigned char`**|**`wchar_t`**|
|`_T` lub `_TEXT`|Brak efektu (usunięty przez preprocesor)|Brak efektu (usunięty przez preprocesor)|`L`(konwertuje następujący znak lub ciąg na odpowiedni odpowiednik Unicode)|

## <a name="see-also"></a>Zobacz także

[Mapowania tekstu ogólnego](../c-runtime-library/generic-text-mappings.md)<br/>
[Stałe i globalne mapowania zmiennych](../c-runtime-library/constant-and-global-variable-mappings.md)<br/>
[Mapowania procedur](../c-runtime-library/routine-mappings.md)<br/>
[Przykładowy program tekstu ogólnego](../c-runtime-library/a-sample-generic-text-program.md)<br/>
[Korzystanie z mapowań tekstu ogólnego](../c-runtime-library/using-generic-text-mappings.md)
