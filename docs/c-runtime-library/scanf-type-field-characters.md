---
title: scanf — Znaki pola typu
ms.date: 11/04/2016
apilocation:
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- scanf
helpviewer_keywords:
- scanf function, type field characters
ms.assetid: 5d546a84-715b-44ca-b1c5-bbe997f9ff62
ms.openlocfilehash: 10783ffd6b4f343e4dd768a01396878c186503fa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390883"
---
# <a name="scanf-type-field-characters"></a>scanf — Znaki pola typu

Poniższe informacje dotyczą dowolnych `scanf` rodziny funkcji, w tym bezpieczne wersje, takie jak `scanf_s`.

`type` Znak jest tylko wymagane pole formatu; prawdopodobnie po wszystkich pól opcjonalne formatu. `type` Znak Określa, czy skojarzona argument jest interpretowany jako znak, ciąg lub liczba.

### <a name="type-characters-for-scanf-functions"></a>Znaki typu dla funkcji scanf

|Znak|Typ danych wejściowych oczekuje|Typ argumentu|Rozmiar argumentu w bezpiecznej wersji?|
|---------------|----------------------------|----------------------|--------------------------------------|
|`c`|znak. Gdy jest używane z `scanf` funkcje, określa znak Jednobajtowy, gdy jest używane z `wscanf` funkcje, określa znaku dwubajtowego. Białe znaki, które zazwyczaj są pomijane podczas odczytu `c` jest określony. Aby odczytać następnego znaku jednobajtowego bez odstępu, należy użyć `%1s`; do odczytania dalej innych niż biały znak dwubajtowy, użyj `%1ws`.|Wskaźnik do `char` gdy jest używane z `scanf` funkcje, wskaźnik do `wchar_t` gdy jest używane z `wscanf` funkcji.|Wymagana. Wartość nie obejmuje miejsca dla terminator o wartości null.|
|`C`|Przeciwne wielkość znaków. Gdy jest używane z `scanf` funkcje, określa znaków dwubajtowych; w przypadku korzystania z `wscanf` funkcje, określa znaków jednobajtowych. Białe znaki, które zazwyczaj są pomijane podczas odczytu `C` jest określony. Aby odczytać następnego znaku jednobajtowego bez odstępu, należy użyć `%1s`; do odczytania dalej innych niż biały znak dwubajtowy, użyj `%1ws`.|Wskaźnik do `wchar_t` gdy jest używane z `scanf` funkcje, wskaźnik do `char` gdy jest używane z `wscanf` funkcji.|Wymagana. Rozmiar argumentu nie ma miejsce terminator o wartości null.|
|`d`|Liczba dziesiętna.|Wskaźnik do `int`.|Nie.|
|`i`|Liczba całkowita. Szesnastkowy, jeśli ciąg wejściowy zaczyna się od "0 x" lub "0 X" ósemkową, jeśli ciąg rozpoczyna się od "0", w przeciwnym razie dziesiętną.|Wskaźnik do `int`.|Nie.|
|`o`|Ósemkowa liczba całkowita.|Wskaźnik do `int`.|Nie.|
|`p`|Adres wskaźnika w cyfr szesnastkowych. Maksymalna liczba cyfr, przeczytaj zależy od rozmiaru wskaźnika (32 lub 64-bitowy), która jest zależna od architektury komputera. "0 x" lub "0 X" będzie akceptowane jako prefiksy.|Wskaźnik do `void*`.|Nie.|
|`u`|Nieoznaczona dziesiętna liczba całkowita.|Wskaźnik do `unsigned int`.|Nie.|
|`x`|Szesnastkowa liczba całkowita.|Wskaźnik do `int`.|Nie.|
|`e`, `E`, `f`, `F`, `g`, `G`|Wartość zmiennoprzecinkowa, składający się z opcjonalnego znaku (+ lub -), serię jeden lub więcej cyfr dziesiętnych, zawierający punktu dziesiętnego i wykładnika opcjonalnie ("e" lub "E"), następuje z wartością całkowitą z zakresu opcjonalnie podpisem.|Wskaźnik do `float`.|Nie.|
|`a`, `A`|Wartość zmiennoprzecinkowa, składający się z szeregu jeden lub więcej cyfr szesnastkowych, zawierające opcjonalnym separatorem dziesiętnym i wykładnik ("p" lub "P"), a następnie wartość dziesiętną.|Wskaźnik do `float`.|Nie.|
|`n`|Nie dane wejściowe odczytane ze strumienia lub buforu.|Wskaźnik do `int`do czyli przechowywanych liczbę znaków, które pomyślnie odczytać ze strumienia i buforować do tego punktu w bieżącym wywołaniu `scanf` funkcji lub `wscanf` funkcji.|Nie.|
|`s`|Ciąg do pierwszego znaku odstępu (spacja, karty lub nowego wiersza). Umożliwiające odczyt ciągów, które nie są rozdzielone spacjami, należy użyć zestawu nawiasami kwadratowymi (`[ ]`), zgodnie z opisem w [scanf — specyfikacje szerokości](../c-runtime-library/scanf-width-specification.md).|Gdy jest używane z `scanf` funkcje, oznacza tablicy znaków jednobajtowych; w przypadku korzystania z `wscanf` funkcje, oznacza tablicy znaków dwubajtowych. W obu przypadkach tablicy znaków musi być wystarczająco duży dla pola wejściowego oraz kończącego znaku null, która jest automatycznie dołączane.|Wymagana. Rozmiar obejmuje miejsce terminator o wartości null.|
|`S`|Rozmiar przeciwieństwem ciąg znaków, maksymalnie pierwszy znak odstępu (spacja, karty lub nowego wiersza). Umożliwiające odczyt ciągów, które nie są rozdzielone spacjami, należy użyć zestawu nawiasami kwadratowymi (`[ ]`), zgodnie z opisem w [scanf — specyfikacje szerokości](../c-runtime-library/scanf-width-specification.md).|Gdy jest używane z `scanf` funkcje, oznacza tablicy znaków dwubajtowych; w przypadku, gdy jest używane z `wscanf` funkcje, oznacza tablicy pojedynczych bajtów znaków. W obu przypadkach tablicy znaków musi być wystarczająco duży dla pola wejściowego oraz kończącego znaku null, która jest automatycznie dołączane.|Wymagana. Rozmiar obejmuje miejsce terminator o wartości null.|

Argumenty rozmiar w razie potrzeby powinien być przekazywany w natychmiast po argumentów, które odnoszą się do listy parametrów. Na przykład poniższy kod:

```
char string1[11], string2[9];
scanf_s("%10s %8s", string1, 11, string2, 9);
```

odczytuje parametry o maksymalnej długości 10 do `string1`i parametry o maksymalnej długości 8 do `string2`. Rozmiar buforów powinien być co najmniej jeden więcej niż specyfikacje szerokości od miejsca musi być zarezerwowana dla terminator o wartości null.

Ciąg formatu, który może obsługiwać wprowadzanie znaków jednobajtowych lub szerokie niezależnie od tego, czy jest używany znaków jednobajtowych lub znaków dwubajtowych wersję funkcji. W związku z tym znaków jednobajtowych lub szerokie, za pomocą `scanf` funkcje i `wscanf` funkcje i używać specyfikatorów formatu w następujący sposób.

|Aby przeczytać znak jako|Aby użyć tej funkcji|Za pomocą tych specyfikatorów formatu|
|--------------------------|-----------------------|----------------------------------|
|jednobajtowe|`scanf` Funkcje|`c`, `hc`, lub `hC`|
|jednobajtowe|`wscanf` Funkcje|`C`, `hc`, lub `hC`|
|szerokie|`wscanf` Funkcje|`c`, `lc`, lub `lC`|
|szerokie|`scanf` Funkcje|`C`, `lc`, lub `lC`|

Skanowanie ciągów `scanf` funkcje, i `wscanf` funkcje, za pomocą powyższej tabeli specyfikatorów typ formatu `s` i `S` zamiast `c` i `C`.

## <a name="see-also"></a>Zobacz także

[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)
