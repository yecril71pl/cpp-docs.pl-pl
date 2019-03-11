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
ms.openlocfilehash: aa6827607430bf8f0db37997bac0223833fcd171
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57747933"
---
# <a name="using-generic-text-mappings"></a>Mapowania zwykłego tekstu

**Microsoft Specific**

Aby uprościć tworzenie kodu na różne rynki międzynarodowe, biblioteki wykonawczej Microsoft przewiduje mapowania "generic-text" specyficzne dla firmy Microsoft wiele typów danych, procedury i innych obiektów. Te mapowania są zdefiniowane w TCHAR. H. Te mapowania nazwy służy do pisania ogólnego kodu, który może być kompilowane dla każdego z trzech typów zestawów znaków: ASCII (SBCS), MBCS lub Unicode, w zależności od stała manifestu, można zdefiniować przy użyciu `#define` instrukcji. Mapowania zwykłego tekstu są rozszerzeniami Microsoft, które nie są zgodny ze standardem ANSI.

### <a name="preprocessor-directives-for-generic-text-mappings"></a>Dyrektywy preprocesora do mapowania zwykłego tekstu

|#define|Skompilowanych wersji|Przykład|
|--------------|----------------------|-------------|
|`_UNICODE`|Unicode (szerokich znaków)|`_tcsrev` Mapuje `_wcsrev`|
|`_MBCS`|Multibyte-character|`_tcsrev` Mapuje `_mbsrev`|
|None (wartość domyślna: ani `_UNICODE` ani `_MBCS` zdefiniowane)|SBCS (ASCII)|`_tcsrev` Mapuje `strrev`|

Na przykład funkcja generic tekst `_tcsrev`zdefiniowaną w TCHAR. Godz., mapuje `mbsrev` Jeśli `MBCS` został zdefiniowany w programie lub do `_wcsrev` Jeśli `_UNICODE` został zdefiniowany. W przeciwnym razie `_tcsrev` mapuje `strrev`.

Typ danych — zwykły tekst `_TCHAR`, również zdefiniowanej w TCHAR. H, mapuje do typu `char` Jeśli `_MBCS` jest zdefiniowana na typ `wchar_t` Jeśli `_UNICODE` jest zdefiniowany i wpisz `char` Jeśli żadna stała jest zdefiniowany. W TCHAR znajdują się inne mapowanie typu danych. Godz. w celu ułatwienia programowania, ale `_TCHAR` to typ, który jest najbardziej przydatne.

### <a name="generic-text-data-type-mappings"></a>Mapowanie typu danych — zwykły tekst

|Nazwa typu danych — zwykły tekst|SBCS (_UNICODE, _MBCS nie zdefiniowano)|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|----------------------------------|--------------------------------------------|--------------------|-----------------------|
|`_TCHAR`|`char`|`char`|`wchar_t`|
|`_TINT`|`int`|`int`|`wint_t`|
|`_TSCHAR`|`signed char`|`signed char`|`wchar_t`|
|`_TUCHAR`|`unsigned char`|`unsigned char`|`wchar_t`|
|`_TXCHAR`|`char`|`unsigned char`|`wchar_t`|
|`_T` lub `_TEXT`|Żadnego skutku (usuwane przez preprocesor)|Żadnego skutku (usuwane przez preprocesor)|`L` (konwertuje zgodnie z jego odpowiednikiem Unicode znak lub ciąg)|

Aby uzyskać pełną listę mapowania typ ogólny tekst procedury, zmienne i innych obiektów, zobacz [mapowania typ ogólny-tekst](../c-runtime-library/generic-text-mappings.md).

Poniższe fragmenty kodu pokazują korzystanie z `_TCHAR` i `_tcsrev` do mapowania do MBCS, Unicode i SBCS modele.

```
_TCHAR *RetVal, *szString;
RetVal = _tcsrev(szString);
```

Jeśli `MBCS` została zdefiniowana, preprocesor mapuje poprzedniego fragmentu z następującym kodem:

```
char *RetVal, *szString;
RetVal = _mbsrev(szString);
```

Jeśli `_UNICODE` została zdefiniowana, preprocesor mapuje tego samego fragmentu z następującym kodem:

```
wchar_t *RetVal, *szString;
RetVal = _wcsrev(szString);
```

Jeśli żadna `_MBCS` ani `_UNICODE` została zdefiniowana, preprocesor mapuje fragment kodowi ASCII jednobajtowe w następujący sposób:

```
char *RetVal, *szString;
RetVal = strrev(szString);
```

Ten sposób można napisać, obsługa i skompiluj plik kodu źródłowego pojedynczej do uruchamiania przy użyciu procedur, które są specyficzne dla żadnego z trzech typów zestawów znaków.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Mapowania zwykłego tekstu](../c-runtime-library/generic-text-mappings.md)<br/>
[Mapowania typu danych](../c-runtime-library/data-type-mappings.md)<br/>
[Mapowania zmiennych globalnych i stałych](../c-runtime-library/constant-and-global-variable-mappings.md)<br/>
[Mapowania procedur](../c-runtime-library/routine-mappings.md)<br/>
[Przykładowy ogólny program tekstowy](../c-runtime-library/a-sample-generic-text-program.md)
