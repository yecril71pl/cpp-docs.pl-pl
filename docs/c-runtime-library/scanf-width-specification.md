---
title: scanf — Specyfikacje szerokości
ms.date: 11/04/2016
api_location:
- msvcr100.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- scanf
helpviewer_keywords:
- scanf function, width specification
ms.assetid: 94b4e8fe-c4a2-4799-8b6c-a2cf28ffb09c
ms.openlocfilehash: 3b00996f3a17ab9298b1edba5a8e60826e19fdcc
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957344"
---
# <a name="scanf-width-specification"></a>scanf — Specyfikacje szerokości

Te informacje dotyczą interpretacji ciągów formatu w `scanf` rodzinie funkcji, w tym z bezpiecznymi wersjami, takimi jak. `scanf_s` Te funkcje zwykle zakładają, że strumień wejściowy jest podzielony na sekwencję tokenów. Tokeny są oddzielone odstępami (spacja, tabulatorem lub znakiem nowego wiersza) albo w przypadku typów liczbowych, przez naturalną końcówkę typu danych liczbowych, jak wskazano w pierwszym znaku, którego nie można przekonwertować na tekst liczbowy. Jednakże specyfikacja szerokości może być używana w celu przeanalizowania danych wejściowych do zatrzymania przed naturalnym końcem tokenu.

Specyfikacja *szerokości* składa się ze znaków między `%` i specyfikatora pola typu, który może zawierać dodatnią liczbę całkowitą o nazwie pola *Szerokość* i co najmniej jeden znak wskazujący rozmiar pola, który może być również traktowane jako modyfikatory typu pola, takie jak wskazanie, czy typ liczby całkowitej jest **Krótki** czy **długi**. Takie znaki są określane jako prefiks rozmiaru.

## <a name="the-width-field"></a>Pole Szerokość

Pole *Width* jest dodatnią liczbą całkowitą dziesiętną kontrolującą maksymalną liczbę znaków, które mają być odczytane dla tego pola. Nie więcej niż *Szerokość* znaków jest konwertowany i przechowywany w odpowiedniej `argument`lokalizacji. Więcej niż *Szerokość* znaków może być odczytywana, jeśli znak odstępu (spacja, tabulator lub nowy wiersz) lub znak, który nie może zostać przekonwertowany zgodnie z danym formatem, występuje przed osiągnięciem *szerokości* .

Specyfikacja szerokości jest oddzielna i różni się od argumentu rozmiaru buforu wymaganego przez bezpieczne wersje tych funkcji (tj `scanf_s` `wscanf_s`., itp.). W poniższym przykładzie Specyfikacja szerokości wynosi 20, co oznacza, że maksymalnie 20 znaków jest odczytywanych ze strumienia wejściowego. Długość buforu wynosi 21, co obejmuje pomieszczenie dla możliwych 20 znaków oraz terminator o wartości null:

```C
char str[21];
scanf_s("%20s", str, 21);
```

Jeśli pole *Szerokość* nie jest używane, `scanf_s` program spróbuje odczytać cały token w ciągu. Jeśli określony rozmiar nie jest wystarczająco duży, aby pomieścić cały token, nic nie zostanie zapisany w ciągu docelowym. Jeśli pole *Szerokość* jest określone, znaki pierwszej *szerokości* w tokenie będą zapisywane w ciągu docelowym wraz z terminatorem wartości null.

## <a name="the-size-prefix"></a>Prefiks rozmiaru

Opcjonalne prefiksy **h**, **l**, **ll**, **I64** `argument` i **l** wskazują rozmiar (długi lub krótki, znak jednobajtowy lub szeroki, w zależności od typu modyfikowanego przez siebie znaków). Te znaki specyfikacji formatu są używane z znakami w `scanf` lub `wscanf` funkcjach, aby określić interpretację argumentów, jak pokazano w poniższej tabeli. Prefiks typu **I64** jest rozszerzeniem firmy Microsoft i nie jest zgodny ze standardem ANSI. Znaki typu i ich znaczenie są opisane w tabeli "znaki typu dla funkcji scanf" w [znakach pola typu scanf](../c-runtime-library/scanf-type-field-characters.md).

> [!NOTE]
> Prefiksy **h**, **l**i **l** są rozszerzeniami firmy Microsoft, gdy są używane z danymi `char`typu.

### <a name="size-prefixes-for-scanf-and-wscanf-format-type-specifiers"></a>Prefiksy rozmiarów dla specyfikatorów typu scanf i wscanf

|Aby określić|Użyj prefiksu|Ze specyfikatorem typu|
|----------------|----------------|-------------------------|
|**double**|**l**|**e**, **e**, **f**, **g**lub **g**|
|**Long Double** (takie same jak Double)|**L**|**e**, **e**, **f**, **g**lub **g**|
|**long int**|**l**|**d**, **i**, **o**, **x**lub **x**|
|**Długa liczba całkowita bez znaku**|**l**|**u**|
|**Long Long**|**wszystki**|**d**, **i**, **o**, **x**lub **x**|
|`short int`|**h**|**d**, **i**, **o**, **x**lub **x**|
|**krótka liczba całkowita bez znaku**|**h**|**u**|
|__**Int64**|**I64**|**d**, **i**, **o**, **u**, **x**lub **x**|
|Jednobajtowy znak z`scanf`|**h**|**c** lub **c**|
|Jednobajtowy znak z`wscanf`|**h**|**c** lub **c**|
|Szeroki znak z`scanf`|**l**|**c** lub **c**|
|Szeroki znak z`wscanf`|**l**|**c**lub **c**|
|Ciąg znaków jednobajtowych z`scanf`|**h**|**s** lub **s**|
|Ciąg znaków jednobajtowych z`wscanf`|**h**|**s** lub **s**|
|Ciąg znaków dwubajtowych z`scanf`|**l**|**s** lub **s**|
|Ciąg znaków dwubajtowych z`wscanf`|**l**|**s** lub **s**|

W poniższych przykładach użyto **h** i **l** z `scanf_s` funkcjami i `wscanf_s` funkcjami:

```C
scanf_s("%ls", &x, 2);     // Read a wide-character string
wscanf_s(L"%hC", &x, 2);    // Read a single-byte character
```

Jeśli w `scanf` rodzinie jest używana niezabezpieczona funkcja, należy pominąć parametr size wskazujący długość buforu poprzedzającego argumentu.

## <a name="reading-undelimited-strings"></a>Odczytywanie nierozdzielanych ciągów

Aby odczytać ciągi, które nie są rozdzielane znakami odstępu, zestaw znaków w nawiasach ( **[]** ) może zostać zastąpiony dla znaku typu **s** (String). Zestaw znaków w nawiasach jest określany jako ciąg kontrolny. Odpowiednie pole wejściowe jest odczytywane do pierwszego znaku, który nie jest wyświetlany w ciągu formantu. Jeśli pierwszy znak w zestawie jest karetką ( **^** ), efekt zostanie odwrócony: Pole danych wejściowych jest odczytywane do pierwszego znaku, który jest wyświetlany w pozostałej części zestawu znaków.

Należy zauważyć, że **element% [a-z]** i **% [z-a]** jest interpretowany jako odpowiednik elementu **% [abcde... z]** . Jest to typowe `scanf` rozszerzenie funkcji, ale należy pamiętać, że standard ANSI nie jest wymagany.

## <a name="reading-unterminated-strings"></a>Odczytywanie niezakończonych ciągów

Aby zapisać ciąg bez przechowywania kończącego znaku null (' \ 0 ' **%** ), użyj specyfikacji <em>n</em>**c** , gdzie *n* jest dziesiętną liczbą całkowitą. W tym przypadku znak typu **c** wskazuje, że argument jest wskaźnikiem do tablicy znaków. Następne *n* znaków są odczytywane ze strumienia wejściowego do określonej lokalizacji i nie jest dołączany znak null (' \ 0 '). Jeśli *n* nie zostanie określony, jego wartość domyślna to 1.

## <a name="when-scanf-stops-reading-a-field"></a>Gdy scanf przestaje odczytywanie pola

`scanf` Funkcja skanuje każde pole wejściowe, znak po znaku. Może przestać odczytywać dane wejściowe określonego pola, zanim osiągnie znak spacji z różnych powodów:

- Osiągnięto określoną szerokość.

- Nie można przekonwertować następnego znaku w określony sposób.

- Następny znak powoduje konflikt ze znakiem w ciągu kontrolnym, który powinien być zgodny.

- Następny znak nie może pojawić się w danym zestawie znaków.

Z dowolnego powodu, gdy `scanf` Funkcja przestaje odczytywanie pola wejściowego, następne pole wejściowe jest uważane za pierwsze, nieprzeczytane. Znak powodujący konflikt, jeśli istnieje, jest uznawany za nieprzeczytany i jest pierwszym znakiem następnego pola wejściowego lub pierwszym znakiem w kolejnych operacjach odczytu strumienia wejściowego.

## <a name="see-also"></a>Zobacz także

[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[Pola specyfikacji formatu dla funkcji wscanf](../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)<br/>
[scanf, znaki pola typu](../c-runtime-library/scanf-type-field-characters.md)<br/>
