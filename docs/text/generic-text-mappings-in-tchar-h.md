---
title: Mapowania tekstu ogólnego w używanie TCHAR. h
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
ms.openlocfilehash: c317e7d67cc3d086dacbe0f24b0103d389afefda
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217301"
---
# <a name="generic-text-mappings-in-tcharh"></a>Mapowania tekstu ogólnego w używanie TCHAR. h

Aby uprościć transportowanie kodu do użytku międzynarodowego, Biblioteka wykonawcza firmy Microsoft zapewnia mapowanie tekstu ogólnego specyficznego dla firmy Microsoft dla wielu typów danych, procedur i innych obiektów. Można użyć tych mapowań, które są zdefiniowane w używanie TCHAR. h, do pisania kodu generycznego, który może być skompilowany dla zestawów znaków jednobajtowych, wielowymiarowych lub Unicode, w zależności od stałej manifestu zdefiniowanej przy użyciu `#define` instrukcji. Mapowania tekstu ogólnego są rozszerzeniami firmy Microsoft, które nie są zgodne ze standardem ANSI.

Korzystając z używanie TCHAR. h, można tworzyć aplikacje z jednym bajtem, zestawem znaków wielostronicowych (MBCS) i Unicode z tego samego źródła. Używanie TCHAR. h definiuje makra (z prefiksem `_tcs` ), które z poprawnymi definicjami preprocesora, mapują do `str` , `_mbs` lub `wcs` funkcje, zgodnie z potrzebami. Aby skompilować MBCS, zdefiniuj symbol `_MBCS` . Aby skompilować kod Unicode, zdefiniuj symbol `_UNICODE` . Aby skompilować jednobajtową aplikację, zdefiniuj nie (domyślnie). Domyślnie program `_UNICODE` jest zdefiniowany dla aplikacji MFC.

`_TCHAR`Typ danych jest zdefiniowany warunkowo w używanie TCHAR. h. Jeśli symbol `_UNICODE` jest zdefiniowany dla kompilacji, `_TCHAR` jest zdefiniowany jako **`wchar_t`** ; w przeciwnym wypadku dla kompilacji z pojedynczym bajtem i MBCS jest zdefiniowany jako **`char`** . ( **`wchar_t`** , podstawowy typ danych Unicode o szerokim znaku, to 16-bitowy odpowiednik do 8 bitów **`signed char`** ). W przypadku aplikacji międzynarodowych należy używać `_tcs` rodziny funkcji, które działają w `_TCHAR` jednostkach, a nie w bajtach. Na przykład `_tcsncpy` kopie `n` `_TCHARs` , nie `n` bajtów.

Ponieważ niektóre funkcje obsługi ciągów z pojedynczym zestawem znaków (SBCS) pobierają (podpisane) **`char*`** Parametry, podczas gdy jest zdefiniowana, wyniki ostrzeżenia kompilatora niezgodność typów `_MBCS` . Istnieją trzy sposoby, aby uniknąć tego ostrzeżenia:

1. Użyj funkcji wbudowanej bezpiecznie typu sekcje thunk w używanie TCHAR. h. Jest to zachowanie domyślne.

1. Używaj bezpośrednich makr w używanie TCHAR. h przez definiowanie `_MB_MAP_DIRECT` w wierszu polecenia. Jeśli to zrobisz, musisz ręcznie dopasować typy. Jest to najszybsza metoda, ale nie jest bezpieczna pod względem typów.

1. Użyj bezpiecznej ze statycznie połączonej biblioteki funkcji sekcje thunk w używanie TCHAR. h. Aby to zrobić, Zdefiniuj stałą `_NO_INLINING` w wierszu polecenia. Jest to najwolniejsza Metoda, ale najbardziej bezpieczna typ.

### <a name="preprocessor-directives-for-generic-text-mappings"></a>Dyrektywy preprocesora dla mapowań tekstu ogólnego

|# Definiuj|Skompilowana wersja|Przykład|
|---------------|----------------------|-------------|
|`_UNICODE`|Unicode (znak dwubajtowy)|`_tcsrev`mapuje do`_wcsrev`|
|`_MBCS`|Znaki wielobajtowe|`_tcsrev`mapuje do`_mbsrev`|
|Brak (wartość domyślna nie ma ani nie została `_UNICODE` `_MBCS` zdefiniowana)|SBCS (ASCII)|`_tcsrev`mapuje do`strrev`|

Na przykład funkcja generyczna tekstu `_tcsrev` , która jest zdefiniowana w używanie TCHAR. h, mapuje do, `_mbsrev` Jeśli została zdefiniowana `_MBCS` w programie lub `_wcsrev` zdefiniowana `_UNICODE` . W przeciwnym razie `_tcsrev` mapuje na `strrev` . Inne mapowania typu danych są dostępne w używanie TCHAR. h na potrzeby wygody programowania, ale `_TCHAR` są najbardziej przydatne.

### <a name="generic-text-data-type-mappings"></a>Mapowanie typu danych tekstu ogólnego

|Tekst ogólny<br /> Nazwa typu danych|_UNICODE &<br /> Nie zdefiniowano _MBCS|_MBCS<br /> Określonych|_UNICODE<br /> Określonych|
|--------------------------------------|----------------------------------------|------------------------|---------------------------|
|`_TCHAR`|**`char`**|**`char`**|**`wchar_t`**|
|`_TINT`|**`int`**|**`unsigned int`**|`wint_t`|
|`_TSCHAR`|**`signed char`**|**`signed char`**|**`wchar_t`**|
|`_TUCHAR`|**`unsigned char`**|**`unsigned char`**|**`wchar_t`**|
|`_TXCHAR`|**`char`**|**`unsigned char`**|**`wchar_t`**|
|`_T` lub `_TEXT`|Brak efektu (usunięty przez preprocesor)|Brak efektu (usunięty przez preprocesor)|`L`(konwertuje następujący znak lub ciąg na odpowiedni odpowiednik Unicode)|

Aby uzyskać listę mapowań tekstu ogólnego procedur, zmiennych i innych obiektów, zobacz [Mapowanie tekstu ogólnego](../c-runtime-library/generic-text-mappings.md) w odwołaniu do biblioteki wykonawczej.

> [!NOTE]
> Nie używaj `str` rodziny funkcji z ciągami Unicode, które mogą zawierać osadzone bajty o wartości null. Podobnie nie należy używać `wcs` rodziny funkcji z ciągami MBCS (lub SBCS).

Poniższe fragmenty kodu ilustrują użycie `_TCHAR` i `_tcsrev` dla mapowania do modeli MBCS, Unicode i SBCS.

```cpp
_TCHAR *RetVal, *szString;
RetVal = _tcsrev(szString);
```

Jeśli `_MBCS` został zdefiniowany, preprocesor mapuje ten fragment na ten kod:

```cpp
char *RetVal, *szString;
RetVal = _mbsrev(szString);
```

Jeśli `_UNICODE` został zdefiniowany, preprocesor mapuje ten fragment na ten kod:

```cpp
wchar_t *RetVal, *szString;
RetVal = _wcsrev(szString);
```

Jeśli ani nie zostały `_MBCS` `_UNICODE` zdefiniowane, preprocesor mapuje fragment na jednobajtowy kod ASCII w następujący sposób:

```cpp
char *RetVal, *szString;
RetVal = strrev(szString);
```

W związku z tym można pisać, konserwować i kompilować plik kodu z pojedynczym źródłem do uruchamiania z procedurami, które są specyficzne dla każdego z trzech rodzajów zestawów znaków.

## <a name="see-also"></a>Zobacz też

[Tekst i ciągi](../text/text-and-strings-in-visual-cpp.md)<br/>
[Korzystanie z używanie TCHAR. H typy danych z kodem _MBCS](../text/using-tchar-h-data-types-with-mbcs-code.md)
