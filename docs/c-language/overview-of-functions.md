---
title: Przegląd funkcji
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++]
- control flow, function calls
ms.assetid: b6f4637f-02b9-49d8-8601-1f886bd2cfb9
ms.openlocfilehash: 1c54dcdeec1bad1ffbd335d411e39c77be0ad961
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56150327"
---
# <a name="overview-of-functions"></a>Przegląd funkcji

Funkcje muszą mieć definicji i powinien mieć deklaracją, mimo że definicję może służyć jako zgłoszenia, jeśli deklaracja pojawia się przed wywołaniem funkcji. Definicja funkcji zawiera treść funkcji — kodu, który jest wykonywany, gdy wywoływana jest funkcja.

Deklaracja funkcji ustanawia nazwy, zwracany typ i atrybuty funkcja, która jest zdefiniowana w innym miejscu w programie. Deklaracja funkcji musi poprzedzać wywołanie do funkcji. Jest to, dlaczego pliki nagłówkowe, zawierająca deklaracje funkcji wykonawczej są uwzględnione w kodzie przed wywołaniem funkcji wykonawczej. Jeśli deklaracja zawiera informacje o typach i liczbę parametrów, deklaracja jest prototypem. Zobacz [prototypy funkcji](../c-language/function-prototypes.md) Aby uzyskać więcej informacji.

Kompilator używa prototypu do porównania z typami argumentów w kolejnych wywołaniach funkcji z parametrów funkcji i konwertowania typy argumentów dla typów parametrów, jeśli zajdzie taka potrzeba.

Wywołanie funkcji przekazuje Kontrola wykonywania od funkcji wywołującej wywołanej funkcji. Argumenty, jeśli są przekazywane przez wartość dla wywoływanej funkcji. Wykonywanie `return` instrukcji w wywołanej funkcja zwraca kontroli i ewentualnie wartość do funkcji wywołującej.

## <a name="see-also"></a>Zobacz także

[Funkcje](../c-language/functions-c.md)
