---
title: Mapowania tekstu ogólnego w tchar.h
ms.date: 11/04/2016
helpviewer_keywords:
- mapping generic-text
- generic-text mappings [C++]
- character sets [C++], generic-text mappings
- Unicode [C++], generic-text mappings
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 01e1bb74-5a01-4093-8720-68b6c1fdda80
ms.openlocfilehash: bf872df2e6fb49e64a973e8799eef98dec1cb472
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361340"
---
# <a name="generic-text-mappings-in-tcharh"></a>Mapowania tekstu ogólnego w tchar.h

Aby uprościć transportowanie kodu do użytku międzynarodowego, biblioteka pracy firmy Microsoft udostępnia mapowania tekstu ogólnego specyficzne dla firmy Microsoft dla wielu typów danych, procedur i innych obiektów. Można użyć tych mapowań, które są zdefiniowane w tchar.h, aby napisać ogólny kod, który może być skompilowany dla zestawów znaków `#define` jednobajtowych, wielobajtowych lub Unicode, w zależności od stałej manifestu, którą definiujesz za pomocą instrukcji. Mapowania tekstu ogólnego są rozszerzeniami firmy Microsoft, które nie są zgodne z ansi.

Za pomocą tchar.h, można tworzyć jednobajtowe, wielobajtowy zestaw znaków (MBCS) i Unicode aplikacji z tych samych źródeł. tchar.h definiuje makra (które mają `_tcs`prefiks), które z poprawnymi definicjami `str`preprocesora, mapują na `_mbs`, lub `wcs` funkcje, w stosownych przypadkach. Aby zbudować MBCS, `_MBCS`zdefiniuj symbol . Aby utworzyć unicode, `_UNICODE`zdefiniuj symbol . Aby utworzyć aplikację jedno bajtową, nie definiuj ani (domyślnie). Domyślnie `_UNICODE` jest zdefiniowany dla aplikacji MFC.

Typ `_TCHAR` danych jest zdefiniowany warunkowo w tchar.h. Jeśli symbol `_UNICODE` jest zdefiniowany `_TCHAR` dla kompilacji, jest zdefiniowany jako **wchar_t**; w przeciwnym razie dla kompilacji jedno bajtowych i MBCS jest on definiowany jako **char**. (**wchar_t**, podstawowy typ danych szerokoznakowych Unicode, jest 16-bitowym odpowiednikiem 8-bitowego **znaku**podpisanego .) W zastosowaniach międzynarodowych należy używać `_tcs` rodziny `_TCHAR` funkcji, które działają w jednostkach, a nie bajtach. Na przykład `_tcsncpy` kopie `n` `_TCHARs`, `n` a nie bajty.

Ponieważ niektóre funkcje obsługi ciągów pojedynczego zestawu znaków bajtów (SBCS) przyjmują `char*` `_MBCS` (podpisane) parametry, wyniki ostrzeżenia kompilatora niezgodności typu po zdefiniowaniu. Istnieją trzy sposoby uniknięcia tego ostrzeżenia:

1. Użyj funkcji inline bezpiecznych dla typu thunks w tchar.h. Jest to zachowanie domyślne.

1. Użyj makr bezpośrednich w tchar.h, definiując `_MB_MAP_DIRECT` w wierszu polecenia. Jeśli to zrobisz, należy ręcznie dopasować typy. Jest to najszybsza metoda, ale nie jest bezpieczna dla typu.

1. Użyj funkcji biblioteki bezpiecznej dla typu statycznie w tchar.h. Aby to zrobić, `_NO_INLINING` należy zdefiniować stałą w wierszu polecenia. Jest to najwolniejsza metoda, ale najbardziej bezpieczna.

### <a name="preprocessor-directives-for-generic-text-mappings"></a>Dyrektywy preprocesora dla mapowań tekstu ogólnego

|# zdefiniuj|Skompilowana wersja|Przykład|
|---------------|----------------------|-------------|
|`_UNICODE`|Unicode (szeroki znak)|`_tcsrev`mapuje do`_wcsrev`|
|`_MBCS`|Znak wielobajtowy|`_tcsrev`mapuje do`_mbsrev`|
|Brak (wartość domyślna `_UNICODE` `_MBCS` nie została zdefiniowana)|SBCS (ASCII)|`_tcsrev`mapuje do`strrev`|

Na przykład `_tcsrev`funkcja tekstu ogólnego , która jest zdefiniowana w `_mbsrev` tchar.h, mapuje do, jeśli zdefiniowano `_MBCS` w programie, lub do `_wcsrev` jeśli zdefiniowano `_UNICODE`. W `_tcsrev` przeciwnym `strrev`razie mapuje do . Inne mapowania typów danych są dostarczane w tchar.h dla wygody programowania, ale `_TCHAR` jest najbardziej przydatne.

### <a name="generic-text-data-type-mappings"></a>Mapowania typów danych tekstu ogólnego

|Tekst ogólny<br /> Nazwa typu danych|_UNICODE &<br /> _MBCS nie zdefiniowano|_mbcs<br /> Zdefiniowane|_unicode<br /> Zdefiniowane|
|--------------------------------------|----------------------------------------|------------------------|---------------------------|
|`_TCHAR`|**char**|**char**|**wchar_t**|
|`_TINT`|**int**|**unsigned int**|`wint_t`|
|`_TSCHAR`|**podpisany znak**|**podpisany znak**|**wchar_t**|
|`_TUCHAR`|**unsigned char**|**unsigned char**|**wchar_t**|
|`_TXCHAR`|**char**|**unsigned char**|**wchar_t**|
|`_T` lub `_TEXT`|Brak efektu (usunięty przez preprocesor)|Brak efektu (usunięty przez preprocesor)|`L`(konwertuje następujący znak lub ciąg na jego odpowiednik Unicode)|

Aby uzyskać listę mapowań tekstu ogólnego procedur, zmiennych i innych obiektów, zobacz [Mapowania tekstu ogólnego](../c-runtime-library/generic-text-mappings.md) w odwołaniu do biblioteki w czasie wykonywania.

> [!NOTE]
> Nie należy `str` używać rodziny funkcji z ciągami Unicode, które mogą zawierać osadzone bajty null. Podobnie nie należy używać `wcs` rodziny funkcji z ciągami MBCS (lub SBCS).

Poniższe fragmenty kodu ilustrują użycie `_TCHAR` i `_tcsrev` mapowanie do modeli MBCS, Unicode i SBCS.

```cpp
_TCHAR *RetVal, *szString;
RetVal = _tcsrev(szString);
```

Jeśli `_MBCS` został zdefiniowany, preprocesor mapuje ten fragment do tego kodu:

```cpp
char *RetVal, *szString;
RetVal = _mbsrev(szString);
```

Jeśli `_UNICODE` został zdefiniowany, preprocesor mapuje ten fragment do tego kodu:

```cpp
wchar_t *RetVal, *szString;
RetVal = _wcsrev(szString);
```

Jeśli żaden `_MBCS` `_UNICODE` z nich nie został zdefiniowany, preprocesor mapuje fragment na jedno bajtowy kod ASCII w następujący sposób:

```cpp
char *RetVal, *szString;
RetVal = strrev(szString);
```

W związku z tym można napisać, zachować i skompilować plik kodu źródłowego do uruchomienia z procedur, które są specyficzne dla dowolnego z trzech rodzajów zestawów znaków.

## <a name="see-also"></a>Zobacz też

[Tekst i ciągi](../text/text-and-strings-in-visual-cpp.md)<br/>
[Używanie typów danych TCHAR.H z kodem _MBCS](../text/using-tchar-h-data-types-with-mbcs-code.md)
