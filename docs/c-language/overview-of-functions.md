---
title: Przegląd funkcji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- functions [C++]
- control flow, function calls
ms.assetid: b6f4637f-02b9-49d8-8601-1f886bd2cfb9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b03357ed094684bb561eff9b790c090a1ebb0712
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033631"
---
# <a name="overview-of-functions"></a>Przegląd funkcji

Funkcje muszą mieć definicji i powinien mieć deklaracją, mimo że definicję może służyć jako zgłoszenia, jeśli deklaracja pojawia się przed wywołaniem funkcji. Definicja funkcji zawiera treść funkcji — kodu, który jest wykonywany, gdy wywoływana jest funkcja.

Deklaracja funkcji ustanawia nazwy, zwracany typ i atrybuty funkcja, która jest zdefiniowana w innym miejscu w programie. Deklaracja funkcji musi poprzedzać wywołanie do funkcji. Jest to, dlaczego pliki nagłówkowe, zawierająca deklaracje funkcji wykonawczej są uwzględnione w kodzie przed wywołaniem funkcji wykonawczej. Jeśli deklaracja zawiera informacje o typach i liczbę parametrów, deklaracja jest prototypem. Zobacz [prototypy funkcji](../c-language/function-prototypes.md) Aby uzyskać więcej informacji.

Kompilator używa prototypu do porównania z typami argumentów w kolejnych wywołaniach funkcji z parametrów funkcji i konwertowania typy argumentów dla typów parametrów, jeśli zajdzie taka potrzeba.

Wywołanie funkcji przekazuje Kontrola wykonywania od funkcji wywołującej wywołanej funkcji. Argumenty, jeśli są przekazywane przez wartość dla wywoływanej funkcji. Wykonywanie `return` instrukcji w wywołanej funkcja zwraca kontroli i ewentualnie wartość do funkcji wywołującej.

## <a name="see-also"></a>Zobacz też

[Funkcje](../c-language/functions-c.md)