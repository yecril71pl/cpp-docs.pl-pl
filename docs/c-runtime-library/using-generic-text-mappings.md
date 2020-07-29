---
title: Mapowania zwykłego tekstu
ms.date: 11/04/2016
f1_keywords:
- _UNICODE
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
- _UNICODE constant
- TXCHAR type
- generic-text mappings
- _TSCHAR type
- T type
- mappings, generic-text
- _TUCHAR type
- MBCS data type
- _MBCS data type
- _TEXT type
- UNICODE constant
- _T type
ms.assetid: 2848121c-e51f-4b9b-a2e6-833ece4b0cb3
ms.openlocfilehash: f8616e0ff660b299544ed3c2f0a12feb4dbfe66b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221877"
---
# <a name="using-generic-text-mappings"></a>Mapowania zwykłego tekstu

**Specyficzne dla firmy Microsoft**

Aby uprościć Programowanie kodu dla różnych rynków międzynarodowych, Biblioteka wykonawcza firmy Microsoft zapewnia specyficzne dla firmy Microsoft mapowania "ogólny-tekst" dla wielu typów danych, procedur i innych obiektów. Mapowania te są zdefiniowane w używanie TCHAR. C. Przy użyciu tych mapowań nazw można napisać kod generyczny, który można skompilować dla dowolnego z trzech rodzajów zestawów znaków: ASCII (SBCS), MBCS lub Unicode, w zależności od stałej manifestu zdefiniowanej przy użyciu `#define` instrukcji. Mapowania tekstu ogólnego są rozszerzeniami firmy Microsoft, które nie są zgodne ze standardem ANSI.

### <a name="preprocessor-directives-for-generic-text-mappings"></a>Dyrektywy preprocesora dla mapowań tekstu ogólnego

|#define|Skompilowana wersja|Przykład|
|--------------|----------------------|-------------|
|`_UNICODE`|Unicode (znak dwubajtowy)|`_tcsrev`mapuje do`_wcsrev`|
|`_MBCS`|Znaki wielobajtowe|`_tcsrev`mapuje do`_mbsrev`|
|Brak (wartość domyślna: nie jest ani `_UNICODE` `_MBCS` zdefiniowana)|SBCS (ASCII)|`_tcsrev`mapuje do`strrev`|

Na przykład funkcja generyczna tekstu `_tcsrev` zdefiniowana w używanie TCHAR. H, mapowanie do `mbsrev` if zostało `MBCS` zdefiniowane w programie lub w `_wcsrev` przypadku, gdy został `_UNICODE` zdefiniowany. W przeciwnym razie `_tcsrev` mapuje na `strrev` .

Typ danych rodzajowych `_TCHAR` , zdefiniowany również w używanie TCHAR. H mapuje do typu, **`char`** Jeśli `_MBCS` jest zdefiniowany, do typu, jeśli **`wchar_t`** `_UNICODE` jest zdefiniowany, i do typu, **`char`** Jeśli żadna stała nie jest zdefiniowana. Inne mapowania typów danych są dostępne w używanie TCHAR. H dla wygody programowania, ale `_TCHAR` jest to najbardziej użyteczny typ.

### <a name="generic-text-data-type-mappings"></a>Mapowanie typu danych tekstu ogólnego

|Nazwa typu danych rodzajowych|SBCS (_UNICODE, _MBCS nie zdefiniowany)|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|----------------------------------|--------------------------------------------|--------------------|-----------------------|
|`_TCHAR`|**`char`**|**`char`**|**`wchar_t`**|
|`_TINT`|**`int`**|**`int`**|`wint_t`|
|`_TSCHAR`|**`signed char`**|**`signed char`**|**`wchar_t`**|
|`_TUCHAR`|**`unsigned char`**|**`unsigned char`**|**`wchar_t`**|
|`_TXCHAR`|**`char`**|**`unsigned char`**|**`wchar_t`**|
|`_T` lub `_TEXT`|Brak efektu (usunięty przez preprocesor)|Brak efektu (usunięty przez preprocesor)|`L`(konwertuje następujący znak lub ciąg na odpowiedni odpowiednik Unicode)|

Aby uzyskać pełną listę mapowań tekstu ogólnego procedur, zmiennych i innych obiektów, zobacz [Mapowanie tekstu ogólnego](../c-runtime-library/generic-text-mappings.md).

Poniższe fragmenty kodu ilustrują użycie `_TCHAR` i `_tcsrev` dla mapowania do modeli MBCS, Unicode i SBCS.

```
_TCHAR *RetVal, *szString;
RetVal = _tcsrev(szString);
```

Jeśli `MBCS` został zdefiniowany, preprocesor mapuje poprzedni fragment do następującego kodu:

```
char *RetVal, *szString;
RetVal = _mbsrev(szString);
```

Jeśli `_UNICODE` został zdefiniowany, preprocesor mapuje ten sam fragment do następującego kodu:

```
wchar_t *RetVal, *szString;
RetVal = _wcsrev(szString);
```

Jeśli ani nie został `_MBCS` `_UNICODE` zdefiniowany, preprocesor mapuje fragment na jednobajtowy kod ASCII w następujący sposób:

```
char *RetVal, *szString;
RetVal = strrev(szString);
```

W ten sposób można pisać, konserwować i kompilować pojedynczy plik kodu źródłowego do uruchamiania z procedurami, które są specyficzne dla każdego z trzech rodzajów zestawów znaków.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Mapowania tekstu ogólnego](../c-runtime-library/generic-text-mappings.md)<br/>
[Mapowania typów danych](../c-runtime-library/data-type-mappings.md)<br/>
[Stałe i globalne mapowania zmiennych](../c-runtime-library/constant-and-global-variable-mappings.md)<br/>
[Mapowania procedur](../c-runtime-library/routine-mappings.md)<br/>
[Przykładowy program tekstu ogólnego](../c-runtime-library/a-sample-generic-text-program.md)
