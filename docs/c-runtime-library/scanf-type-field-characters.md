---
title: scanf — Znaki pola typu
ms.date: 11/04/2016
helpviewer_keywords:
- scanf function, type field characters
ms.assetid: 5d546a84-715b-44ca-b1c5-bbe997f9ff62
ms.openlocfilehash: dbc6142a87bee00b130589fef5ab92a44f189864
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444751"
---
# <a name="scanf-type-field-characters"></a>scanf — Znaki pola typu

Poniższe informacje dotyczą dowolnych z `scanf` rodziny funkcji, w tym bezpiecznych wersji, takich jak `scanf_s`.

Znak `type` jest jedynym wymaganym polem formatu; pojawia się po dowolnych opcjonalnych pól formatu. Znak `type` określa, czy skojarzony argument jest interpretowany jako znak, ciąg czy liczba.

### <a name="type-characters-for-scanf-functions"></a>Znaki typu dla funkcji scanf

|Znak|Oczekiwany typ danych wejściowych|Typ argumentu|Czy rozmiar argumentu w bezpiecznej wersji?|
|---------------|----------------------------|----------------------|--------------------------------------|
|`c`|Opis. Gdy jest używany z funkcjami `scanf`, określa znak jednobajtowy; w przypadku używania z funkcjami `wscanf`, określa znak dwubajtowy. Znaki odstępu, które są normalnie pomijane, są odczytywane po określeniu `c`. Aby odczytać następny znak niebędący odstępem jednobajtowy, użyj `%1s`; Aby przeczytać następny znak niebędący odstępem, użyj `%1ws`.|Wskaźnik do `char`, gdy jest używany z funkcjami `scanf`, wskaźnik do `wchar_t`, gdy jest używany z funkcjami `wscanf`.|Wymagany. Rozmiar nie zawiera spacji dla terminatora o wartości null.|
|`C`|Przeciwieństwo znaku rozmiaru. Gdy jest używany z funkcjami `scanf`, określa znak dwubajtowy; gdy jest używany z funkcjami `wscanf`, określa znak jednobajtowy. Znaki odstępu, które są normalnie pomijane, są odczytywane po określeniu `C`. Aby odczytać następny znak niebędący odstępem jednobajtowy, użyj `%1s`; Aby przeczytać następny znak niebędący odstępem, użyj `%1ws`.|Wskaźnik do `wchar_t`, gdy jest używany z funkcjami `scanf`, wskaźnik do `char`, gdy jest używany z funkcjami `wscanf`.|Wymagany. Argument size nie zawiera spacji dla terminatora o wartości null.|
|`d`|Liczba całkowita dziesiętna.|Wskaźnik do `int`.|Nie.|
|`i`|Liczba całkowita. Szesnastkowy, jeśli ciąg wejściowy zaczyna się od "0x" lub "0X", ósemkowego, jeśli ciąg rozpoczyna się od "0", w przeciwnym razie Decimal.|Wskaźnik do `int`.|Nie.|
|`o`|Ósemkowa liczba całkowita.|Wskaźnik do `int`.|Nie.|
|`p`|Adres wskaźnika w postaci cyfr szesnastkowych. Maksymalna liczba odczytanych cyfr zależy od rozmiaru wskaźnika (32 lub 64 bitów), który zależy od architektury komputera. "0x" lub "0X" są akceptowane jako prefiksy.|Wskaźnik do `void*`.|Nie.|
|`u`|Liczba całkowita dziesiętna bez znaku.|Wskaźnik do `unsigned int`.|Nie.|
|`x`|Szesnastkowa liczba całkowita.|Wskaźnik do `int`.|Nie.|
|`e`, `E`, `f`, `F`, `g``G`|Wartość zmiennoprzecinkowa składająca się z opcjonalnego znaku (+ lub-), serii z co najmniej jednej cyfry dziesiętnej zawierającej separator dziesiętny oraz opcjonalnego wykładnika ("e" lub "E"), po której następuje opcjonalnie wartość całkowita ze znakiem.|Wskaźnik do `float`.|Nie.|
|`a`, `A`|Wartość zmiennoprzecinkowa składająca się z serii co najmniej jednej cyfry szesnastkowej zawierającej opcjonalny punkt dziesiętny oraz wykładnik ("p" lub "P"), po którym następuje wartość dziesiętna.|Wskaźnik do `float`.|Nie.|
|`n`|Brak danych wejściowych odczytywanych z strumienia lub buforu.|Wskaźnik do `int`, w którym jest przechowywana liczba znaków pomyślnie odczytywanych ze strumienia lub buforem do tego momentu w bieżącym wywołaniu funkcji `scanf` Functions lub `wscanf` Functions.|Nie.|
|`s`|Ciąg, do pierwszego znaku odstępu (spacja, karta lub nowy wiersz). Aby odczytać ciągi, które nie są rozdzielane znakami spacji, użyj zestawu nawiasów kwadratowych (`[ ]`), jak opisano w [specyfikacji szerokości scanf](../c-runtime-library/scanf-width-specification.md).|Gdy jest używany z funkcjami `scanf`, oznacza tablicę znaków jednobajtowych; w przypadku używania z funkcjami `wscanf`, oznacza tablicę znaków dwubajtowych. W obu przypadkach tablica znaków musi być wystarczająco duża dla pola wejściowego i kończącego znak null, który jest automatycznie dołączany.|Wymagany. Rozmiar obejmuje miejsce dla terminatora o wartości null.|
|`S`|Ciąg znaków w przeciwieństwie do rozmiaru, do pierwszego znaku odstępu (spacja, karta lub nowy wiersz). Aby odczytać ciągi, które nie są rozdzielane znakami spacji, użyj zestawu nawiasów kwadratowych (`[ ]`), jak opisano w [specyfikacji szerokości scanf](../c-runtime-library/scanf-width-specification.md).|Gdy jest używany z funkcjami `scanf`, oznacza tablicę znaków dwubajtowych; gdy jest używany z funkcjami `wscanf`, oznacza tablicę o pojedynczym bajcie. W obu przypadkach tablica znaków musi być wystarczająco duża dla pola wejściowego i kończącego znak null, który jest automatycznie dołączany.|Wymagany. Rozmiar obejmuje miejsce dla terminatora o wartości null.|

Argumenty rozmiaru, jeśli jest to wymagane, powinny być przekazane do listy parametrów bezpośrednio po argumencie, do którego mają zastosowanie. Na przykład następujący kod:

```
char string1[11], string2[9];
scanf_s("%10s %8s", string1, 11, string2, 9);
```

odczytuje ciąg z maksymalną długością 10 do `string1`i ciągiem o maksymalnej długości 8 do `string2`. Rozmiary buforów powinny mieć co najmniej jedną wartość, ponieważ przestrzeń musi być zarezerwowana dla terminatora o wartości null.

Ciąg formatu może obsługiwać wprowadzanie jednobajtowe lub szerokie, niezależnie od tego, czy jest używana funkcja jednobajtowego znaku, czy też wersja znaku większości. W tym celu należy odczytywać znaki jednobajtowe lub szerokie z funkcjami `scanf` i funkcjami `wscanf`, używając specyfikatorów formatu w następujący sposób.

|Aby odczytać znak jako|Użyj tej funkcji|Z tymi specyfikatorami formatu|
|--------------------------|-----------------------|----------------------------------|
|jednobajtowe|`scanf`, funkcje|`c`, `hc`lub `hC`|
|jednobajtowe|`wscanf`, funkcje|`C`, `hc`lub `hC`|
|szerokie|`wscanf`, funkcje|`c`, `lc`lub `lC`|
|szerokie|`scanf`, funkcje|`C`, `lc`lub `lC`|

Aby skanować ciągi przy użyciu funkcji `scanf` i funkcji `wscanf`, użyj powyższej tabeli z specyfikatorami typu format `s` i `S` zamiast `c` i `C`.

## <a name="see-also"></a>Zobacz też

[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)
