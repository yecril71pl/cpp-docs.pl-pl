---
title: scanf — Specyfikacje szerokości
ms.date: 11/04/2016
apilocation:
- msvcr100.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- scanf
helpviewer_keywords:
- scanf function, width specification
ms.assetid: 94b4e8fe-c4a2-4799-8b6c-a2cf28ffb09c
ms.openlocfilehash: 1431002a7e7d0054ac20c05c76b05cabc96177c5
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743265"
---
# <a name="scanf-width-specification"></a>scanf — Specyfikacje szerokości

Te informacje dotyczą interpretacji ciągów formatu w `scanf` rodziny funkcji, takich jak tym bezpieczne wersje `scanf_s`. Te funkcje zwykle założono, że strumień wejściowy jest podzielona na sekwencja tokeny. Tokeny są rozdzielone przez odstępu (miejsca, tabulatorem ani) lub w przypadku typów wartości liczbowych, do końca naturalnych typu dane liczbowe, wskazane przez pierwszy znak, który nie można konwertować wartości liczbowych. Jednak specyfikacje szerokości można spowodować, że podczas analizowania danych wejściowych można zatrzymać przed zakończeniem naturalnych tokenu.

*Szerokość* specyfikacji zawiera znaki między `%` i specyfikator pola typu mogą obejmować dodatnią liczbą całkowitą o nazwie *szerokość* pola oraz jeden lub więcej znaków rozmiar pola, które mogą być również uwzględnione jako modyfikatory typu pola, takie jak wskazanie, czy jest typu Liczba całkowita wskazująca **krótki** lub **długie**. Takie znaki są określane jako prefiks rozmiaru.

## <a name="the-width-field"></a>Szerokość pola

*Szerokość* pole jest dodatnia dziesiętną liczbą całkowitą kontrolowanie maksymalna liczba znaków do odczytu dla tego pola. Nie więcej niż *szerokość* znaki są konwertowane i przechowywane w odpowiednich `argument`. Mniej niż *szerokość* znaki mogą być odczytu, jeśli znak odstępu (miejsca, tabulatorem ani) lub znak, który nie może zostać skonwertowany zgodnie z danego formatu występuje przed *szerokość* zostanie osiągnięty.

Specyfikacja szerokości jest odrębne i niezależne od argumentu rozmiaru buforu, które są wymagane przez bezpieczne wersje tych funkcji (czyli `scanf_s`, `wscanf_s`itp.). W poniższym przykładzie, specyfikacje szerokości wynosi 20, co oznacza, że do 20 znaków mają być odczytane ze strumienia wejściowego. Długość buforu jest 21, w tym pomieszczeniu możliwe 20 znaków oraz terminator o wartości null:

```C
char str[21];
scanf_s("%20s", str, 21);
```

Jeśli *szerokość* pole nie jest używane, `scanf_s` podejmie próbę odczytu całego token do ciągu. Jeśli określony rozmiar jest wystarczająco duży, aby pomieścić całą tokenu, nic nie zostanie zapisany do ciągu docelowego. Jeśli *szerokość* pola jest określony, następnie pierwszy *szerokość* znakami w tokenie zostanie zapisany do ciągu docelowego wraz z terminatorem null.

## <a name="the-size-prefix"></a>Rozmiar przedrostka

Opcjonalne prefiksy parametru **h**, **l**, **ll**, **I64**, i **L** wskazywać wielkość `argument`(długi lub krótki, znaków jednobajtowych lub znaków dwubajtowych, w zależności od znaku typu, który modyfikuje). Te znaki specyfikacji formatu są używane wraz z typów znaków w `scanf` lub `wscanf` funkcji do określenia interpretacji argumentów, jak pokazano w poniższej tabeli. Prefiks typu **I64** jest rozszerzeniem firmy Microsoft i nie jest ANSI zgodny. Znaki typu i ich znaczenie są opisane w tabeli "Typ znaków dla funkcji scanf" [scanf — znaki pola typu](../c-runtime-library/scanf-type-field-characters.md).

> [!NOTE]
> **h**, **l**, i **L** prefiksy są rozszerzeniami Microsoft, gdy jest używane z danymi typu `char`.

### <a name="size-prefixes-for-scanf-and-wscanf-format-type-specifiers"></a>Rozmiar prefiksów dla scanf i wscanf specyfikatorów typ formatu

|Aby określić|Użyj prefiksu|Ze specyfikatorem typu|
|----------------|----------------|-------------------------|
|**double**|**l**|**e**, **E**, **f**, **g**, lub **G**|
|**double** (tak samo, jak double)|**L**|**e**, **E**, **f**, **g**, lub **G**|
|**long int**|**l**|**d**, **i**, **o**, **x**, lub **X**|
|**Long unsigned int**|**l**|**u**|
|**długi długi**|**ll**|**d**, **i**, **o**, **x**, lub **X**|
|`short int`|**h**|**d**, **i**, **o**, **x**, lub **X**|
|**krótka wartość całkowita bez znaku**|**h**|**u**|
|__**int64**|**I64**|**d**, **i**, **o**, **u**, **x**, lub **X**|
|Znak Jednobajtowy, za pomocą `scanf`|**h**|**c** lub **C**|
|Znak Jednobajtowy, za pomocą `wscanf`|**h**|**c** lub **C**|
|Znak dwubajtowy, za pomocą `scanf`|**l**|**c** lub **C**|
|Znak dwubajtowy, za pomocą `wscanf`|**l**|**c**, lub **C**|
|Jednobajtowe — ciąg znaków `scanf`|**h**|**s** lub **S**|
|Jednobajtowe — ciąg znaków `wscanf`|**h**|**s** lub **S**|
|Ciąg znaków dwubajtowych `scanf`|**l**|**s** lub **S**|
|Ciąg znaków dwubajtowych `wscanf`|**l**|**s** lub **S**|

W poniższych przykładach używane **h** i **l** z `scanf_s` funkcje i `wscanf_s` funkcje:

```C
scanf_s("%ls", &x, 2);     // Read a wide-character string
wscanf_s(L"%hC", &x, 2);    // Read a single-byte character
```

Jeśli funkcja niezabezpieczonych w `scanf` rodziny, pominięto parametr rozmiaru wskazujący długość buforu poprzedniego argumentu.

## <a name="reading-undelimited-strings"></a>Odczytywanie Undelimited ciągów

Umożliwiające odczyt ciągów, które nie są rozdzielane znakami odstępu znaków, zestaw znaków w nawiasach kwadratowych (**[**) mogą zastąpić **s** znaku typu (ciąg). Zestaw znaków w nawiasach jest określany jako ciąg formantu. Odpowiednie pole danych wejściowych jest do odczytu do pierwszego znaku, który nie jest widoczna w ciągu kontroli. Jeśli pierwszy znak w zestawie jest znak daszka (**^**), zostanie odwrócony wpływ: Pola wejściowego jest do odczytu do pierwszego znaku, który jest widoczna w pozostałej części zestawu znaków.

Należy pamiętać, że **% [a-z]** i **% [z-]** są interpretowane jako równoważne **% [abcde... z]**. Jest to często `scanf` rozszerzenie funkcji, ale należy pamiętać, że ANSI standard nie wymaga.

## <a name="reading-unterminated-strings"></a>Niezakończony odczyt ciągów

Aby ciąg bez przechowywania kończącego znaku null ('\0'), należy użyć specyfikacji **%** <em>n</em>**c** gdzie *n* jest dziesiętną liczbą całkowitą. W tym przypadku **c** znaku typu wskazuje, że argument jest wskaźnikiem do tablicy znaków. Następne *n* znaki są odczytywane ze strumienia wejściowego do określonej lokalizacji, a nie znakiem null ('\0') jest dołączany. Jeśli *n* nie zostanie określony, jego wartość domyślna to 1.

## <a name="when-scanf-stops-reading-a-field"></a>Gdy scanf zatrzymuje odczytanie pola

`scanf` Funkcja skanuje każde pole wejściowe, znak po znaku. Może się zatrzymać, odczytu określonego pola wejściowego, przed osiągnięciem przez nią znak spacji różnych powodów:

- Określona szerokość został osiągnięty.

- Nie można przekonwertować następny znak określone.

- Następny znak powoduje konflikt z znak w ciągu formant, który powinien odpowiadać.

- Następny znak nie są wyświetlane w danego zestawu znaków.

Z jakiegokolwiek powodu gdy `scanf` funkcja przestaje odczytywanie pola wejściowego, dalej pola wejściowego jest uważany za rozpocząć przy pierwszym znaku, jako nieprzeczytane. Znak powodujące konflikt, jeśli istnieje, jest traktowany jako nieprzeczytane i jest pierwszym znakiem następne pole wejściowe lub pierwszy znak w kolejnych operacji odczytu dla strumienia wejściowego.

## <a name="see-also"></a>Zobacz także

[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[Pola specyfikacji formatu dla funkcji wscanf](../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)<br/>
[scanf, znaki pola typu](../c-runtime-library/scanf-type-field-characters.md)<br/>
