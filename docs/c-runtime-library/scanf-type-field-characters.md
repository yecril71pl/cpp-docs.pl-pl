---
title: scanf — Znaki pola typu
ms.date: 11/04/2016
api_location:
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- scanf
helpviewer_keywords:
- scanf function, type field characters
ms.assetid: 5d546a84-715b-44ca-b1c5-bbe997f9ff62
ms.openlocfilehash: 86b57aff9cba5065c7c8053dc26e63e3c0cae169
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957834"
---
# <a name="scanf-type-field-characters"></a>scanf — Znaki pola typu

Poniższe informacje dotyczą którejkolwiek `scanf` z rodzin funkcji, w tym bezpiecznych wersji, takich jak. `scanf_s`

`type` Znak jest jedynym wymaganym polem formatu, który jest wyświetlany po dowolnych polach w formacie opcjonalnym. `type` Znak określa, czy skojarzony argument jest interpretowany jako znak, ciąg lub liczba.

### <a name="type-characters-for-scanf-functions"></a>Znaki typu dla funkcji scanf

|Znak|Oczekiwany typ danych wejściowych|Typ argumentu|Czy rozmiar argumentu w bezpiecznej wersji?|
|---------------|----------------------------|----------------------|--------------------------------------|
|`c`|Opis. Gdy jest używany `scanf` z funkcjami, określa znak jednobajtowy; gdy jest `wscanf` używany z funkcjami, określa szeroki znak. Po `c` określeniu znaków odstępu, które są normalnie pomijane, są odczytywane. Aby odczytać następny znak niebędący odstępem jednobajtowym, użyj `%1s`;, aby odczytać następny znak niebędący odstępem, użyj `%1ws`.|Wskaźnik do `char` , gdy jest `scanf` używany z funkcjami, `wchar_t` wskaźnikiem do `wscanf` , gdy jest używany z funkcjami.|Wymagane. Rozmiar nie zawiera spacji dla terminatora o wartości null.|
|`C`|Przeciwieństwo znaku rozmiaru. Gdy jest używany `scanf` z funkcjami, określa znak dwubajtowy; `wscanf` gdy jest używany z funkcjami, określa znak pojedynczy. Po `C` określeniu znaków odstępu, które są normalnie pomijane, są odczytywane. Aby odczytać następny znak niebędący odstępem jednobajtowym, użyj `%1s`;, aby odczytać następny znak niebędący odstępem, użyj `%1ws`.|Wskaźnik do `wchar_t` , gdy jest `scanf` używany z funkcjami, `char` wskaźnikiem do `wscanf` , gdy jest używany z funkcjami.|Wymagana. Argument size nie zawiera spacji dla terminatora o wartości null.|
|`d`|Liczba całkowita dziesiętna.|Wskaźnik na `int`.|Nie.|
|`i`|Liczba całkowita. Szesnastkowy, jeśli ciąg wejściowy zaczyna się od "0x" lub "0X", ósemkowego, jeśli ciąg rozpoczyna się od "0", w przeciwnym razie Decimal.|Wskaźnik na `int`.|Nie.|
|`o`|Ósemkowa liczba całkowita.|Wskaźnik na `int`.|Nie.|
|`p`|Adres wskaźnika w postaci cyfr szesnastkowych. Maksymalna liczba odczytanych cyfr zależy od rozmiaru wskaźnika (32 lub 64 bitów), który zależy od architektury komputera. "0x" lub "0X" są akceptowane jako prefiksy.|Wskaźnik na `void*`.|Nie.|
|`u`|Liczba całkowita dziesiętna bez znaku.|Wskaźnik na `unsigned int`.|Nie.|
|`x`|Szesnastkowa liczba całkowita.|Wskaźnik na `int`.|Nie.|
|`e`, `E`, `f`, `F`, `g`, `G`|Wartość zmiennoprzecinkowa składająca się z opcjonalnego znaku (+ lub-), serii z co najmniej jednej cyfry dziesiętnej zawierającej separator dziesiętny oraz opcjonalnego wykładnika ("e" lub "E"), po której następuje opcjonalnie wartość całkowita ze znakiem.|Wskaźnik na `float`.|Nie.|
|`a`, `A`|Wartość zmiennoprzecinkowa składająca się z serii co najmniej jednej cyfry szesnastkowej zawierającej opcjonalny punkt dziesiętny oraz wykładnik ("p" lub "P"), po którym następuje wartość dziesiętna.|Wskaźnik na `float`.|Nie.|
|`n`|Brak danych wejściowych odczytywanych z strumienia lub buforu.|Wskaźnik do `int`, w którym przechowywana jest liczba znaków, które zostały pomyślnie odczytane ze strumienia lub buforu do tego punktu w `scanf` bieżącym wywołaniu `wscanf` funkcji lub funkcji.|Nie.|
|`s`|Ciąg, do pierwszego znaku odstępu (spacja, karta lub nowy wiersz). Aby odczytać ciągi, które nie są rozdzielane znakami spacji, należy użyć zestawu`[ ]`nawiasów kwadratowych (), jak opisano w [specyfikacji szerokości scanf](../c-runtime-library/scanf-width-specification.md).|Gdy jest używany `scanf` z funkcjami, oznacza tablicę znaków jednobajtowych; gdy jest `wscanf` używana z funkcjami, oznacza tablicę znaków szerokich. W obu przypadkach tablica znaków musi być wystarczająco duża dla pola wejściowego i kończącego znak null, który jest automatycznie dołączany.|Wymagana. Rozmiar obejmuje miejsce dla terminatora o wartości null.|
|`S`|Ciąg znaków w przeciwieństwie do rozmiaru, do pierwszego znaku odstępu (spacja, karta lub nowy wiersz). Aby odczytać ciągi, które nie są rozdzielane znakami spacji, należy użyć zestawu`[ ]`nawiasów kwadratowych (), jak opisano w [specyfikacji szerokości scanf](../c-runtime-library/scanf-width-specification.md).|Gdy jest używany `scanf` z funkcjami, oznacza tablicę szerokich znaków; w przypadku `wscanf` używania z funkcjami oznacza tablicę jednobajtową znaków. W obu przypadkach tablica znaków musi być wystarczająco duża dla pola wejściowego i kończącego znak null, który jest automatycznie dołączany.|Wymagana. Rozmiar obejmuje miejsce dla terminatora o wartości null.|

Argumenty rozmiaru, jeśli jest to wymagane, powinny być przekazane do listy parametrów bezpośrednio po argumencie, do którego mają zastosowanie. Na przykład następujący kod:

```
char string1[11], string2[9];
scanf_s("%10s %8s", string1, 11, string2, 9);
```

odczytuje ciąg z maksymalną długością 10 do `string1`i ciąg z maksymalną długością 8 do. `string2` Rozmiary buforów powinny mieć co najmniej jedną wartość, ponieważ przestrzeń musi być zarezerwowana dla terminatora o wartości null.

Ciąg formatu może obsługiwać wprowadzanie jednobajtowe lub szerokie, niezależnie od tego, czy jest używana funkcja jednobajtowego znaku, czy też wersja znaku większości. W ten sposób, aby odczytywać znaki jednobajtowe `scanf` lub szerokie `wscanf` z funkcjami i funkcjami, użyj specyfikatorów formatu w następujący sposób.

|Aby odczytać znak jako|Użyj tej funkcji|Z tymi specyfikatorami formatu|
|--------------------------|-----------------------|----------------------------------|
|jednobajtowe|`scanf`, funkcje|`c`, `hc`lub`hC`|
|jednobajtowe|`wscanf`, funkcje|`C`, `hc`lub`hC`|
|szerokie|`wscanf`, funkcje|`c`, `lc`lub`lC`|
|szerokie|`scanf`, funkcje|`C`, `lc`lub`lC`|

Aby skanować ciągi przy `scanf` użyciu funkcji i `wscanf` funkcji, użyj powyższej tabeli z `c` specyfikatorami typu `s` format i `S` zamiast i `C`.

## <a name="see-also"></a>Zobacz także

[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)
