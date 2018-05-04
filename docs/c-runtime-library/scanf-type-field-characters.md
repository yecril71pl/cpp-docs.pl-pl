---
title: scanf — znaki pola typu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
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
dev_langs:
- C++
helpviewer_keywords:
- scanf function, type field characters
ms.assetid: 5d546a84-715b-44ca-b1c5-bbe997f9ff62
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb4c1c25c5b45fc967954ea78a35a9420b712f81
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="scanf-type-field-characters"></a>scanf — Znaki pola typu
Poniższe informacje dotyczą poszczególnych `scanf` rodzinę funkcji, w tym bezpiecznego wersje, takie jak `scanf_s`.  
  
 `type` Znak jest jedynym wymagane pole format; wydaje się po wszystkie pola opcjonalne formatu. `type` Znaku Określa, czy skojarzony argument jest interpretowana jako znak, ciąg lub liczba.  
  
### <a name="type-characters-for-scanf-functions"></a>Znaki typu dla funkcji scanf  
  
|Znak|Typ danych wejściowych jest oczekiwana|Typ argumentu|Rozmiar argumentu w bezpiecznej wersji?|  
|---------------|----------------------------|----------------------|--------------------------------------|  
|`c`|Znak. W przypadku użycia z `scanf` funkcje, określa znaków jednobajtowych; w przypadku użycia z `wscanf` funkcje, określa znaków dwubajtowych. Białe znaki, które zwykle są pomijane są odczytywane podczas `c` jest określona. Aby odczytać następny z systemem innym niż biały znak jednobajtowe, użyj `%1s`; do odczytania dalej z systemem innym niż biały znak całego, użyj `%1ws`.|Wskaźnik do `char` w przypadku użycia z `scanf` funkcji, wskaźnik do `wchar_t` w przypadku użycia z `wscanf` funkcji.|Wymagana. Wartość nie obejmuje miejsca dla terminatora o wartości null.|  
|`C`|Przeciwne wielkość znaków. W przypadku użycia z `scanf` funkcje, określa znaków typu wide; w przypadku użycia z `wscanf` funkcje, określa znaków. Białe znaki, które zwykle są pomijane są odczytywane podczas `C` jest określona. Aby odczytać następny z systemem innym niż biały znak jednobajtowe, użyj `%1s`; do odczytania dalej z systemem innym niż biały znak całego, użyj `%1ws`.|Wskaźnik do `wchar_t` w przypadku użycia z `scanf` funkcji, wskaźnik do `char` w przypadku użycia z `wscanf` funkcji.|Wymagana. Rozmiar argumentu nie obejmuje miejsca dla terminatora o wartości null.|  
|`d`|Dziesiętną liczbą całkowitą.|Wskaźnik do `int`.|Nie.|  
|`i`|Liczba całkowita. Szesnastkowy, jeśli ciąg wejściowy rozpoczyna się od "0 x" lub "0 X" ósemkową, jeżeli ciąg rozpoczyna się od "0", w przeciwnym razie wartość dziesiętną.|Wskaźnik do `int`.|Nie.|  
|`o`|Ósemkową liczby całkowitej.|Wskaźnik do `int`.|Nie.|  
|`p`|Adres wskaźnika w cyfr szesnastkowych. Maksymalna liczba cyfr, przeczytaj zależy od rozmiaru wskaźnika (32- lub 64-bitowy), która jest zależna od architektury komputera. "0 x" lub "0 X" są akceptowane jako prefiksy.|Wskaźnik do `void*`.|Nie.|  
|`u`|Dziesiętną liczbą całkowitą bez znaku.|Wskaźnik do `unsigned int`.|Nie.|  
|`x`|Liczba całkowita szesnastkową.|Wskaźnik do `int`.|Nie.|  
|`e`, `E`, `f`, `F`, `g`, `G`|Wartość zmiennoprzecinkowa składające się z opcjonalne znak (+ lub -), serii jeden lub więcej cyfr dziesiętnych zawierające dziesiętnego i wykładnik opcjonalne ("e" lub "E"), a następnie opcjonalnie podpisem liczbę całkowitą z przedziału.|Wskaźnik do `float`.|Nie.|  
|`a`, `A`|Wartość zmiennoprzecinkowa składające się z serii jeden lub więcej cyfr szesnastkowych zawierający opcjonalnym separatorem dziesiętnym i wykładnik ("p" lub "P"), a następnie wartości dziesiętnej.|Wskaźnik do `float`.|Nie.|  
|`n`|Nie wprowadzono odczytu ze strumienia lub buforu.|Wskaźnik do `int`, do przechowywanej liczba znaków, która jest pomyślnie odczytane ze strumienia lub bufor do tego punktu w bieżącym wywołaniu `scanf` funkcji lub `wscanf` funkcji.|Nie.|  
|`s`|Ciąg do pierwszego znaku spacji (miejsca, karty lub nowego wiersza). Aby odczytać ciągów nie są rozdzielone spacjami, należy użyć zestawu nawiasy kwadratowe (`[ ]`), zgodnie z opisem w [scanf — specyfikacje szerokości](../c-runtime-library/scanf-width-specification.md).|W przypadku użycia z `scanf` funkcje, oznacza, że tablica znaków; w przypadku użycia z `wscanf` funkcje, oznacza, że tablica znaków dwubajtowych. W obu przypadkach tablicy znaków musi być wystarczająco duży dla pola wejściowego oraz znak końcowy null, która jest automatycznie dołączane.|Wymagana. Rozmiar obejmuje miejsca dla terminatora o wartości null.|  
|`S`|Przeciwieństwem rozmiar ciągu znaków do pierwszego znaku spacji (miejsca, karty lub nowego wiersza). Aby odczytać ciągów nie są rozdzielone spacjami, należy użyć zestawu nawiasy kwadratowe (`[ ]`), zgodnie z opisem w [scanf — specyfikacje szerokości](../c-runtime-library/scanf-width-specification.md).|W przypadku użycia z `scanf` funkcje, oznacza, że tablica znaków dwubajtowych; w przypadku użycia z `wscanf` funkcje, oznacza, że tablica bajtów jednoznakowym. W obu przypadkach tablicy znaków musi być wystarczająco duży dla pola wejściowego oraz znak końcowy null, która jest automatycznie dołączane.|Wymagana. Rozmiar obejmuje miejsca dla terminatora o wartości null.|  
  
  
 Na liście parametrów bezpośrednio po argumentu, które dotyczą one powinien zostać przekazany argumenty rozmiar w razie potrzeby. Na przykład następujący kod:  
  
```  
char string1[11], string2[9];  
scanf_s("%10s %8s", string1, 11, string2, 9);  
```  
  
 odczytuje ciągiem o maksymalnej długości 10 do `string1`, a ciąg o maksymalnej długości od 8 do `string2`. Rozmiar buforu powinien być co najmniej jeden więcej niż specyfikacje szerokości od miejsca musi być zarezerwowana dla terminatorem null.  
  
 Ciąg formatu, który może obsługiwać wprowadzanie znaków jednobajtowych lub szerokie, niezależnie od tego, czy używany jest znaków jednobajtowych lub wersji znaków dwubajtowych w funkcji. W związku z tym można odczytać znaki jednobajtowe lub szerokie z `scanf` funkcje i `wscanf` funkcje, użyj specyfikatory formatu w następujący sposób.  
  
|Aby odczytać znak jako|Użyj tej funkcji|Z tych specyfikatory formatu|  
|--------------------------|-----------------------|----------------------------------|  
|jednobajtowe|`scanf` Funkcje|`c`, `hc`, lub `hC`|  
|jednobajtowe|`wscanf` Funkcje|`C`, `hc`, lub `hC`|  
|szerokie|`wscanf` Funkcje|`c`, `lc`, lub `lC`|  
|szerokie|`scanf` Funkcje|`C`, `lc`, lub `lC`|  
  
 Skanowanie ciągów `scanf` funkcje, i `wscanf` funkcji, należy użyć powyższej tabeli z specyfikatory typ formatu `s` i `S` zamiast `c` i `C`.  
  
## <a name="see-also"></a>Zobacz też  
 [scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)