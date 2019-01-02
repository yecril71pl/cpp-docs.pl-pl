---
title: Mapowania typ ogólny tekst w pliku tchar.h
ms.date: 11/04/2016
f1_keywords:
- tchar.h
helpviewer_keywords:
- mapping generic-text
- generic-text mappings [C++]
- character sets [C++], generic-text mappings
- Unicode [C++], generic-text mappings
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 01e1bb74-5a01-4093-8720-68b6c1fdda80
ms.openlocfilehash: 59df523cc553881186921a878d131a109ae3cf27
ms.sourcegitcommit: fe1e21df175cd004d21c6e4659082efceb649a8b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53978299"
---
# <a name="generic-text-mappings-in-tcharh"></a>Mapowania typ ogólny tekst w pliku tchar.h

Aby uprościć transport kodu do użytku międzynarodowego, biblioteki wykonawczej Microsoft przewiduje mapowania typ ogólny tekst specyficzne dla firmy Microsoft wiele typów danych, procedury i innych obiektów. Możesz użyć tych mapowań, które są zdefiniowane w pliku tchar.h, aby napisać kod ogólny, który może być kompilowane dla pojedynczych bajtów, wielobajtowego, lub zestawy znaków Unicode, w zależności od stała manifestu, który zdefiniujesz przy użyciu `#define` instrukcji. Mapowania zwykłego tekstu są rozszerzeniami Microsoft, które nie są zgodny ze standardem ANSI.

Za pomocą tchar.h, można utworzyć zestawu znaków wielobajtowych (MBCS), aplikacji nieobsługujących kodu Unicode z tego samego źródła i jednobajtowych. Tchar.h definiuje makra (które mają prefiks `_tcs`), za pomocą prawidłowe definicje preprocesora, mapowanie na `str`, `_mbs`, lub `wcs` funkcje, zgodnie z potrzebami. Aby skompilować MBCS, zdefiniuj symbol `_MBCS`. Aby skompilować Unicode, zdefiniuj symbol `_UNICODE`. Aby skompilować aplikację jednobajtowych, zdefiniuj ani (ustawienie domyślne). Domyślnie `_UNICODE` jest zdefiniowana dla aplikacji MFC.

`_TCHAR` Typ danych jest zdefiniowany w pliku tchar.h w warunkowo. Jeśli symbol `_UNICODE` jest zdefiniowany dla kompilacji, `_TCHAR` jest zdefiniowany jako **wchar_t**; w przeciwnym razie jednobajtowe i MBCS kompilacji jest zdefiniowana jako **char**. (**wchar_t**, podstawowy typ danych szerokich znaków Unicode jest odpowiednikiem 16-bitowych do 8-bitowej podpisanej **char**.) Aplikacje międzynarodowe, można użyć `_tcs` rodziny funkcji, które działają w `_TCHAR` jednostek, nie w bajtach. Na przykład `_tcsncpy` kopie `n` `_TCHARs`, a nie `n` bajtów.

Ponieważ niektóre ciąg jednego bajtu znaków Ustaw (SBCS) — Obsługa funkcji take (z podpisem) `char*` parametrów, typu spowoduje ostrzeżenia kompilatora niezgodność podczas `_MBCS` jest zdefiniowana. Istnieją trzy sposoby, aby uniknąć tego ostrzeżenia:

1. W pliku tchar.h, należy użyć sekcje Thunk funkcji bezpiecznego typu wbudowanego. Jest to zachowanie domyślne.

1. Użyj makra bezpośrednie w pliku tchar.h, definiując `_MB_MAP_DIRECT` w wierszu polecenia. Jeśli to zrobisz, musisz ręcznie dopasować typów. To najszybszy sposób, ale nie jest bezpieczny.

1. Użyj sekcje Thunk funkcji bezpiecznego typu statycznie połączoną bibliotekę, w pliku tchar.h. Aby to zrobić, należy zdefiniować stałą `_NO_INLINING` w wierszu polecenia. Jest to metoda najwolniejsze, ale najbardziej bezpieczny.

### <a name="preprocessor-directives-for-generic-text-mappings"></a>Dyrektywy preprocesora do mapowania zwykłego tekstu

|Zdefiniuj #|Skompilowanych wersji|Przykład|
|---------------|----------------------|-------------|
|`_UNICODE`|Unicode (szerokich znaków)|`_tcsrev` Mapuje `_wcsrev`|
|`_MBCS`|Znak wielobajtowy|`_tcsrev` Mapuje `_mbsrev`|
|Brak (domyślnie nie ma `_UNICODE` ani `_MBCS` zdefiniowane)|SBCS (ASCII)|`_tcsrev` Mapuje `strrev`|

Na przykład funkcja generic tekst `_tcsrev`, która została zdefiniowana w tchar.h, mapy do `_mbsrev` Jeśli zdefiniowano `_MBCS` w programie lub do `_wcsrev` Jeśli zdefiniowano `_UNICODE`. W przeciwnym razie `_tcsrev` mapuje `strrev`. Inne mapowanie typu danych znajdują się w pliku tchar.h w celu ułatwienia programowania, ale `_TCHAR` jest najbardziej użyteczna.

### <a name="generic-text-data-type-mappings"></a>Mapowanie typu danych — zwykły tekst

|Zwykły tekst<br /> Nazwa typu danych|_UNICODE &AMP;<br /> _MBCS niezdefiniowane|_MBCS<br /> Definicja|_UNICODE<br /> Definicja|
|--------------------------------------|----------------------------------------|------------------------|---------------------------|
|`_TCHAR`|**char**|**char**|**wchar_t**|
|`_TINT`|**int**|**unsigned int**|`wint_t`|
|`_TSCHAR`|**podpisany char**|**podpisany char**|**wchar_t**|
|`_TUCHAR`|**unsigned char**|**unsigned char**|**wchar_t**|
|`_TXCHAR`|**char**|**unsigned char**|**wchar_t**|
|`_T` lub `_TEXT`|Żadnego skutku (usuwane przez preprocesor)|Żadnego skutku (usuwane przez preprocesor)|`L` (konwertuje następujący znak lub ciąg z jego odpowiednikiem Unicode)|

Aby uzyskać listę mapowania typ ogólny tekst procedury, zmienne i innych obiektów, zobacz [mapowania typ ogólny-tekst](../c-runtime-library/generic-text-mappings.md) w odwołaniu biblioteki wykonawczej.

> [!NOTE]
>  Nie używaj `str` rodzinę funkcji z ciągów Unicode, które mogą zawierać osadzonych bajty o wartości null. Podobnie, nie używaj `wcs` rodziny funkcji z ciągami MBCS (lub SBCS).

Poniższe fragmenty kodu pokazują korzystanie z `_TCHAR` i `_tcsrev` do mapowania do MBCS, Unicode i SBCS modele.

```cpp
_TCHAR *RetVal, *szString;
RetVal = _tcsrev(szString);
```

Jeśli `_MBCS` została zdefiniowana, preprocesor mapuje ten fragment ten kod:

```cpp
char *RetVal, *szString;
RetVal = _mbsrev(szString);
```

Jeśli `_UNICODE` została zdefiniowana, preprocesor mapuje ten fragment ten kod:

```cpp
wchar_t *RetVal, *szString;
RetVal = _wcsrev(szString);
```

Jeśli żadna `_MBCS` ani `_UNICODE` zostały zdefiniowane, preprocesor mapuje fragment kodowi ASCII jednobajtowe w następujący sposób:

```cpp
char *RetVal, *szString;
RetVal = strrev(szString);
```

W związku z tym można napisać, obsługa i skompiluj plik kodu źródłowego dla pojedynczego, do uruchamiania przy użyciu procedur, które są specyficzne dla żadnego z trzech typów zestawów znaków.

## <a name="see-also"></a>Zobacz też

[Tekst i ciągi](../text/text-and-strings-in-visual-cpp.md)<br/>
[Używanie typów danych TCHAR.H z kodem _MBCS](../text/using-tchar-h-data-types-with-mbcs-code.md)
