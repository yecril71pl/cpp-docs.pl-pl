---
title: scanf — Znaki pola typu
ms.date: 11/04/2016
helpviewer_keywords:
- scanf function, type field characters
ms.assetid: 5d546a84-715b-44ca-b1c5-bbe997f9ff62
ms.openlocfilehash: 8ea5f53f5c6039cf15836ba995df0d63bd6fcb23
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233902"
---
# <a name="scanf-type-field-characters"></a>scanf — Znaki pola typu

Poniższe informacje dotyczą którejkolwiek z `scanf` rodzin funkcji, w tym bezpiecznych wersji, takich jak `scanf_s` .

`type`Znak jest jedynym wymaganym polem formatu, który jest wyświetlany po dowolnych polach w formacie opcjonalnym. `type`Znak określa, czy skojarzony argument jest interpretowany jako znak, ciąg lub liczba.

### <a name="type-characters-for-scanf-functions"></a>Znaki typu dla funkcji scanf

|Znak|Oczekiwany typ danych wejściowych|Typ argumentu|Czy rozmiar argumentu w bezpiecznej wersji?|
|---------------|----------------------------|----------------------|--------------------------------------|
|`c`|Opis. Gdy jest używany z `scanf` funkcjami, określa znak jednobajtowy; gdy jest używany z `wscanf` funkcjami, określa szeroki znak. Po określeniu znaków odstępu, które są normalnie pomijane, są odczytywane `c` . Aby odczytać następny znak niebędący odstępem jednobajtowym, użyj `%1s` ;, aby odczytać następny znak niebędący odstępem, użyj `%1ws` .|Wskaźnik do **`char`** , gdy jest używany z `scanf` funkcjami, wskaźnikiem do, **`wchar_t`** gdy jest używany z `wscanf` funkcjami.|Wymagany. Rozmiar nie zawiera spacji dla terminatora o wartości null.|
|`C`|Przeciwieństwo znaku rozmiaru. Gdy jest używany z `scanf` funkcjami, określa znak dwubajtowy; gdy jest używany z `wscanf` funkcjami, określa znak pojedynczy. Po określeniu znaków odstępu, które są normalnie pomijane, są odczytywane `C` . Aby odczytać następny znak niebędący odstępem jednobajtowym, użyj `%1s` ;, aby odczytać następny znak niebędący odstępem, użyj `%1ws` .|Wskaźnik do **`wchar_t`** , gdy jest używany z `scanf` funkcjami, wskaźnikiem do, **`char`** gdy jest używany z `wscanf` funkcjami.|Wymagany. Argument size nie zawiera spacji dla terminatora o wartości null.|
|`d`|Liczba całkowita dziesiętna.|Wskaźnik na **`int`** .|Nie.|
|`i`|Liczba całkowita. Szesnastkowy, jeśli ciąg wejściowy zaczyna się od "0x" lub "0X", ósemkowego, jeśli ciąg rozpoczyna się od "0", w przeciwnym razie Decimal.|Wskaźnik na **`int`** .|Nie.|
|`o`|Ósemkowa liczba całkowita.|Wskaźnik na **`int`** .|Nie.|
|`p`|Adres wskaźnika w postaci cyfr szesnastkowych. Maksymalna liczba odczytanych cyfr zależy od rozmiaru wskaźnika (32 lub 64 bitów), który zależy od architektury komputera. "0x" lub "0X" są akceptowane jako prefiksy.|Wskaźnik na **`void*`** .|Nie.|
|`u`|Liczba całkowita dziesiętna bez znaku.|Wskaźnik na **`unsigned int`** .|Nie.|
|`x`|Szesnastkowa liczba całkowita.|Wskaźnik na **`int`** .|Nie.|
|`e`, `E`, `f`, `F`, `g`, `G`|Wartość zmiennoprzecinkowa składająca się z opcjonalnego znaku (+ lub-), serii z co najmniej jednej cyfry dziesiętnej zawierającej separator dziesiętny oraz opcjonalnego wykładnika ("e" lub "E"), po której następuje opcjonalnie wartość całkowita ze znakiem.|Wskaźnik na **`float`** .|Nie.|
|`a`, `A`|Wartość zmiennoprzecinkowa składająca się z serii co najmniej jednej cyfry szesnastkowej zawierającej opcjonalny punkt dziesiętny oraz wykładnik ("p" lub "P"), po którym następuje wartość dziesiętna.|Wskaźnik na **`float`** .|Nie.|
|`n`|Brak danych wejściowych odczytywanych z strumienia lub buforu.|Wskaźnik do **`int`** , w którym przechowywana jest liczba znaków, które zostały pomyślnie odczytane ze strumienia lub buforu do tego punktu w bieżącym wywołaniu `scanf` funkcji lub `wscanf` funkcji.|Nie.|
|`s`|Ciąg, do pierwszego znaku odstępu (spacja, karta lub nowy wiersz). Aby odczytać ciągi, które nie są rozdzielane znakami spacji, należy użyć zestawu nawiasów kwadratowych ( `[ ]` ), jak opisano w [specyfikacji szerokości scanf](../c-runtime-library/scanf-width-specification.md).|Gdy jest używany z `scanf` funkcjami, oznacza tablicę znaków jednobajtowych; gdy jest używana z `wscanf` funkcjami, oznacza tablicę znaków szerokich. W obu przypadkach tablica znaków musi być wystarczająco duża dla pola wejściowego i kończącego znak null, który jest automatycznie dołączany.|Wymagany. Rozmiar obejmuje miejsce dla terminatora o wartości null.|
|`S`|Ciąg znaków w przeciwieństwie do rozmiaru, do pierwszego znaku odstępu (spacja, karta lub nowy wiersz). Aby odczytać ciągi, które nie są rozdzielane znakami spacji, należy użyć zestawu nawiasów kwadratowych ( `[ ]` ), jak opisano w [specyfikacji szerokości scanf](../c-runtime-library/scanf-width-specification.md).|Gdy jest używany z `scanf` funkcjami, oznacza tablicę szerokich znaków; w przypadku używania z `wscanf` funkcjami oznacza tablicę jednobajtową znaków. W obu przypadkach tablica znaków musi być wystarczająco duża dla pola wejściowego i kończącego znak null, który jest automatycznie dołączany.|Wymagany. Rozmiar obejmuje miejsce dla terminatora o wartości null.|

Argumenty rozmiaru, jeśli jest to wymagane, powinny być przekazane do listy parametrów bezpośrednio po argumencie, do którego mają zastosowanie. Na przykład następujący kod:

```
char string1[11], string2[9];
scanf_s("%10s %8s", string1, 11, string2, 9);
```

odczytuje ciąg z maksymalną długością 10 do `string1` i ciąg z maksymalną długością 8 do `string2` . Rozmiary buforów powinny mieć co najmniej jedną wartość, ponieważ przestrzeń musi być zarezerwowana dla terminatora o wartości null.

Ciąg formatu może obsługiwać wprowadzanie jednobajtowe lub szerokie, niezależnie od tego, czy jest używana funkcja jednobajtowego znaku, czy też wersja znaku większości. W ten sposób, aby odczytywać znaki jednobajtowe lub szerokie z `scanf` funkcjami i `wscanf` funkcjami, użyj specyfikatorów formatu w następujący sposób.

|Aby odczytać znak jako|Użyj tej funkcji|Z tymi specyfikatorami formatu|
|--------------------------|-----------------------|----------------------------------|
|jednobajtowe|`scanf`, funkcje|`c`, `hc` lub`hC`|
|jednobajtowe|`wscanf`, funkcje|`C`, `hc` lub`hC`|
|szerokie|`wscanf`, funkcje|`c`, `lc` lub`lC`|
|szerokie|`scanf`, funkcje|`C`, `lc` lub`lC`|

Aby skanować ciągi przy użyciu `scanf` funkcji i `wscanf` funkcji, użyj powyższej tabeli z specyfikatorami typu format `s` i `S` zamiast `c` i `C` .

## <a name="see-also"></a>Zobacz także

[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)
