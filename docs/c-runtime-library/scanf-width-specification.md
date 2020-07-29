---
title: scanf, specyfikacja szerokości
ms.date: 10/22/2019
helpviewer_keywords:
- scanf function, width specification
ms.assetid: 94b4e8fe-c4a2-4799-8b6c-a2cf28ffb09c
ms.openlocfilehash: 781e292140babd61fbcde77cefcb917736b17cc3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87188742"
---
# <a name="scanf-width-specification"></a>`scanf`Specyfikacja szerokości

Te informacje dotyczą interpretacji ciągów formatu w `scanf` rodzinie funkcji, w tym z bezpiecznymi wersjami, takimi jak `scanf_s` . Te funkcje zwykle zakładają, że strumień wejściowy jest podzielony na sekwencję tokenów. Tokeny są oddzielone odstępami (spacja, tabulatorem lub znakiem nowego wiersza) lub dla typów numerycznych przez naturalny koniec liczbowego typu danych wskazywanego przez pierwszy znak, który nie może zostać skonwertowany na tekst liczbowy. Jednakże specyfikacja szerokości może być używana w celu przeanalizowania danych wejściowych do zatrzymania przed naturalnym końcem tokenu.

Specyfikacja *szerokości* składa się ze znaków między `%` i specyfikatora pola typu, który może zawierać dodatnią liczbę całkowitą o nazwie pola *Szerokość* i co najmniej jeden znak wskazujący rozmiar pola, który może być również traktowany jako modyfikatory typu pola, takie jak wskazanie, czy typ liczba całkowita to **`short`** czy **`long`** . Takie znaki są określane jako prefiks rozmiaru.

## <a name="the-width-field"></a>Pole Szerokość

Pole *Width* jest dodatnią liczbą całkowitą dziesiętną, która określa maksymalną liczbę znaków do odczytania dla tego pola. Nie więcej niż *Szerokość* znaków jest konwertowany i przechowywany w odpowiednim elemencie `argument` . Można odczytać mniej niż *Szerokość* znaków, jeśli znak odstępu lub znak, który nie może zostać przekonwertowany zgodnie z danym formatem, występuje przed osiągnięciem *szerokości* .

Specyfikacja szerokości jest oddzielna i różni się od argumentu rozmiaru buforu wymaganego przez bezpieczne wersje tych funkcji (na przykład, `scanf_s` , `wscanf_s` i tak dalej). W poniższym przykładzie Specyfikacja szerokości wynosi 20, co oznacza, że maksymalnie 20 znaków jest odczytywanych ze strumienia wejściowego. Długość buforu wynosi 21, co obejmuje pomieszczenie dla możliwych 20 znaków oraz terminator o wartości null:

```C
char str[21];
scanf_s("%20s", str, 21);
```

Jeśli pole *Szerokość* nie jest używane, `scanf_s` próbuje odczytać cały token w ciągu. Jeśli określony rozmiar nie jest wystarczająco duży, aby pomieścić cały token, nic nie jest zapisywane w ciągu docelowym. Jeśli pole *Szerokość* jest określone, wówczas znaki pierwszej *szerokości* w tokenie są zapisywane w ciągu docelowym, wraz z terminatorem wartości null.

## <a name="the-size-prefix"></a>Prefiks rozmiaru

Opcjonalne prefiksy **h**, **hh**, **l**, **ll**, **I64**i **l** wskazują rozmiar `argument` (długi lub krótki, jednobajtowy znak lub szeroki, w zależności od typu modyfikowanego przez siebie znaków). Te znaki specyfikacji formatu są używane z znakami w `scanf` lub `wscanf` funkcjach, aby określić interpretację argumentów, jak pokazano w poniższej tabeli. Prefiks typu **I64** jest rozszerzeniem firmy Microsoft i nie jest zgodny ze standardowym C. Znaki typu i ich znaczenie są opisane w tabeli "znaki typu dla funkcji scanf" w [ `scanf` znakach pola typu](../c-runtime-library/scanf-type-field-characters.md).

> [!NOTE]
> Prefiksy **h**, **l**i **l** są rozszerzeniami firmy Microsoft, gdy są używane z danymi typu **`char`** .

### <a name="size-prefixes-for-scanf-and-wscanf-format-type-specifiers"></a>Prefiksy rozmiarów dla `scanf` `wscanf` specyfikatorów typu i formatu

|Aby określić|Użyj prefiksu|Ze specyfikatorem typu|
|----------------|----------------|-------------------------|
|**`double`**|**&**|**e**, **e**, **f**, **g**lub **g**|
|**`long double`**(analogicznie jak **`double`** )|**L**|**e**, **e**, **f**, **g**lub **g**|
|**`long int`**|**&**|**d**, **i**, **o**, **x**lub **x**|
|**`long unsigned int`**|**&**|**'t**|
|**`long long`**|**wszystki**|**d**, **i**, **o**, **x**lub **x**|
|**`short int`**|**c**|**d**, **i**, **o**, **x**lub **x**|
|**`short unsigned int`**|**c**|**'t**|
|**`char`**|**formacie**|**d**, **i**, **o**, **x**lub **x**|
|**`unsigned char`**|**formacie**|**'t**|
|**`int64`**|**I64**|**d**, **i**, **o**, **u**, **x**lub **x**|
|Jednobajtowy znak z`scanf`|**c**|**c** lub **c**|
|Jednobajtowy znak z`wscanf`|**c**|**c** lub **c**|
|Szeroki znak z`scanf`|**&**|**c** lub **c**|
|Szeroki znak z`wscanf`|**&**|**c**lub **c**|
|Jednobajtowy ciąg znaków z`scanf`|**c**|**s** lub **s**|
|Jednobajtowy ciąg znaków z`wscanf`|**c**|**s** lub **s**|
|Ciąg znaków dwubajtowych z`scanf`|**&**|**s** lub **s**|
|Ciąg znaków dwubajtowych z`wscanf`|**&**|**s** lub **s**|

W poniższych przykładach użyto **h** i **l** z `scanf_s` funkcjami i `wscanf_s` funkcjami:

```C
scanf_s("%ls", &x, 2);     // Read a wide-character string
wscanf_s(L"%hC", &x, 2);    // Read a single-byte character
```

Jeśli w rodzinie jest używana niezabezpieczona funkcja `scanf` , należy pominąć parametr size wskazujący długość buforu poprzedzającego argumentu.

## <a name="reading-undelimited-strings"></a>Odczytywanie nierozdzielanych ciągów

Aby odczytać ciągi, które nie są rozdzielane znakami odstępu, zestaw znaków w nawiasach ( **`[ ]`** ) może zostać zastąpiony dla znaku typu **s** (String). Zestaw znaków w nawiasach jest określany jako *ciąg kontrolny*. Odpowiednie pole wejściowe jest odczytywane do pierwszego znaku, który nie jest wyświetlany w ciągu formantu. Jeśli pierwszy znak w zestawie jest karetką ( **`^`** ), efekt jest odwrócony: pole wejściowe jest odczytywane do pierwszego znaku, który jest wyświetlany w pozostałej części zestawu znaków.

Oba elementy **% [a-z]** i **% [z-a]** są interpretowane jako równoważne z **% [abcde... z]**. Jest to typowe `scanf` rozszerzenie funkcji, ale nie jest wymagane w standardowym języku C.

## <a name="reading-unterminated-strings"></a>Odczytywanie niezakończonych ciągów

Aby zapisać ciąg bez przechowywania kończącego znaku null (' \ 0 '), użyj specyfikacji `%Nc` , gdzie *N* jest dziesiętną liczbą całkowitą. W tym przypadku znak typu **c** wskazuje, że argument jest wskaźnikiem do tablicy znaków. Następne *N* znaków są odczytywane ze strumienia wejściowego do określonej lokalizacji i nie jest dołączany znak null (' \ 0 '). Jeśli *N* nie jest określony, jego wartość domyślna to 1.

## <a name="when-scanf-stops-reading-a-field"></a>Gdy `scanf` kończy odczytywanie pola

`scanf`Funkcja skanuje każde pole wejściowe, znak po znaku. Może przestać odczytywać dane wejściowe określonego pola, zanim osiągnie znak spacji z jednego z kilku powodów:

- Osiągnięto określoną szerokość.

- Nie można przekonwertować następnego znaku w określony sposób.

- Następny znak powoduje konflikt ze znakiem w ciągu kontrolnym, który powinien być zgodny.

- Następny znak nie może pojawić się w danym zestawie znaków.

Z dowolnego powodu, gdy `scanf` Funkcja przestaje odczytywanie pola wejściowego, następne pole wejściowe jest uważane za pierwsze, nieprzeczytane. Znak powodujący konflikt, jeśli istnieje, jest uznawany za nieprzeczytany. Jest to pierwszy znak następnego pola wejściowego lub pierwszy znak w kolejnych operacjach odczytu strumienia wejściowego.

## <a name="see-also"></a>Zobacz także

[`scanf`, `_scanf_l`, `wscanf`, `_wscanf_l`](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[`scanf_s`, `_scanf_s_l`, `wscanf_s`, `_wscanf_s_l`](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[Pola specyfikacji formatu: `scanf` i `wscanf` funkcje](../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)<br/>
[`scanf`Znaki pola typu](../c-runtime-library/scanf-type-field-characters.md)<br/>
