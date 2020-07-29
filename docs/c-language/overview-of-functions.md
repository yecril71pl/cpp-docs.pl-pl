---
title: Przegląd funkcji
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++]
- control flow, function calls
ms.assetid: b6f4637f-02b9-49d8-8601-1f886bd2cfb9
ms.openlocfilehash: 89c9f24b049ee8e9a33557f3262cd6abcc624957
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217067"
---
# <a name="overview-of-functions"></a>Przegląd funkcji

Funkcje muszą mieć definicję i powinny mieć deklarację, chociaż definicja może pełnić rolę deklaracji, jeśli deklaracja jest wyświetlana przed wywołaniem funkcji. Definicja funkcji zawiera treść funkcji — kod, który jest wykonywany po wywołaniu funkcji.

Deklaracja funkcji określa nazwę, zwracany typ i atrybuty funkcji zdefiniowanej w innym miejscu programu. Deklaracja funkcji musi poprzedzać wywołanie funkcji. To dlatego, że pliki nagłówkowe zawierające deklaracje dla funkcji czasu wykonywania są uwzględniane w kodzie przed wywołaniem funkcji run-time. Jeśli deklaracja zawiera informacje o typach i liczbie parametrów, deklaracja jest prototypem. Aby uzyskać więcej informacji, zobacz [prototypy funkcji](../c-language/function-prototypes.md) .

Kompilator używa prototypu do porównywania typów argumentów w kolejnych wywołaniach funkcji z parametrami funkcji i do konwersji typów argumentów do typów parametrów w miarę potrzeb.

Wywołanie funkcji przekazuje sterowanie wykonywaniem z funkcji wywołującej do wywołanej funkcji. Argumenty, jeśli istnieją, są przekazane przez wartość do wywołanej funkcji. Wykonanie **`return`** instrukcji w wywołanej funkcji zwraca kontrolę i prawdopodobnie wartość funkcji wywołującej.

## <a name="see-also"></a>Zobacz także

[Funkcje](../c-language/functions-c.md)
