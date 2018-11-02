---
title: Przegląd funkcji
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++]
- control flow, function calls
ms.assetid: b6f4637f-02b9-49d8-8601-1f886bd2cfb9
ms.openlocfilehash: 3b2f2cfe5cd769b3cdaef002a970ad21c48162ac
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557368"
---
# <a name="overview-of-functions"></a>Przegląd funkcji

Funkcje muszą mieć definicji i powinien mieć deklaracją, mimo że definicję może służyć jako zgłoszenia, jeśli deklaracja pojawia się przed wywołaniem funkcji. Definicja funkcji zawiera treść funkcji — kodu, który jest wykonywany, gdy wywoływana jest funkcja.

Deklaracja funkcji ustanawia nazwy, zwracany typ i atrybuty funkcja, która jest zdefiniowana w innym miejscu w programie. Deklaracja funkcji musi poprzedzać wywołanie do funkcji. Jest to, dlaczego pliki nagłówkowe, zawierająca deklaracje funkcji wykonawczej są uwzględnione w kodzie przed wywołaniem funkcji wykonawczej. Jeśli deklaracja zawiera informacje o typach i liczbę parametrów, deklaracja jest prototypem. Zobacz [prototypy funkcji](../c-language/function-prototypes.md) Aby uzyskać więcej informacji.

Kompilator używa prototypu do porównania z typami argumentów w kolejnych wywołaniach funkcji z parametrów funkcji i konwertowania typy argumentów dla typów parametrów, jeśli zajdzie taka potrzeba.

Wywołanie funkcji przekazuje Kontrola wykonywania od funkcji wywołującej wywołanej funkcji. Argumenty, jeśli są przekazywane przez wartość dla wywoływanej funkcji. Wykonywanie `return` instrukcji w wywołanej funkcja zwraca kontroli i ewentualnie wartość do funkcji wywołującej.

## <a name="see-also"></a>Zobacz też

[Funkcje](../c-language/functions-c.md)