---
title: Konwersje rzutowania typów
ms.date: 11/04/2016
helpviewer_keywords:
- data type conversion [C++], type-cast conversions
- conversions [C++], type-cast
- type casts
- explicit type conversions
- type casts [C++], about type-cast conversion
- type-cast conversions [C++]
ms.assetid: 57ab5902-f12f-4326-a2f6-6282f1d4025a
ms.openlocfilehash: d2de646d9ad3082c43ce896fdf4bc3c7e55a4405
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505306"
---
# <a name="type-cast-conversions"></a>Konwersje rzutowania typów

Rzutowania typów umożliwia jawne konwertowanie typów.

**Składnia**

*wyrażenie CAST*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie jednoargumentowe*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(***nazwy typu***)***wyrażenie cast*

*Nazwa typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikator kwalifikator listy* *abstrakcyjny declarator*<sub>zoptymalizowany pod kątem</sub>

*Nazwy typu* jest typem i *wyrażenie cast* wartość ma zostać przekonwertowany do tego typu. Wyrażenia z rzutowanie typu nie jest l wartością. *Wyrażenie cast* jest konwertowany tak, jakby były przypisane do zmiennej typu *nazwy typu*. Reguły konwersji dla przypisania (opisane w temacie [konwersje przypisań](../c-language/assignment-conversions.md)) dotyczą również rzutowania typu. W poniższej tabeli przedstawiono typy, które mogą być rzutowane do dowolnego typu.

### <a name="legal-type-casts"></a>Rzutowania typów prawne

|Typy docelowego|Potencjalne źródła|
|-----------------------|-----------------------|
|Typy całkowite|Dowolnego typu liczby całkowitej lub typu zmiennoprzecinkowego lub wskaźnik do obiektu|
|Zmiennoprzecinkowe|Dowolny typ arytmetyczny|
|Wskaźnik do obiektu, lub (**void** <strong>\*</strong>)|Dowolnego typu liczby całkowitej (**void** <strong>\*</strong>), wskaźnik do obiektu lub wskaźnika funkcji|
|Wskaźnik funkcji|Dowolnego typu całkowitego, wskaźnik do obiektu lub wskaźnika funkcji|
|Struktura, Unia lub tablicy|Brak|
|Typ void|Dowolnego typu|

Może być rzutowany jakiegokolwiek identyfikatora `void` typu. Jeśli typ określony w wyrażeniu rzutowanie typu nie jest jednak `void`, a następnie identyfikatora rzutowany czy typ nie może być `void` wyrażenia. Każde wyrażenie może być rzutowany `void`, ale wyrażenia typu `void` nie można rzutować do jakichkolwiek innych typów. Na przykład funkcji z `void` zwracać typ nie może mieć jego powrotu rzutowanie do innego typu.

Należy pamiętać, że **void** <strong>\*</strong> wyrażenie zawiera typ wskaźnika do `void`, nie `void`. Jeśli obiekt jest rzutowany na `void` typu wyrażenie wynikowe nie można przypisać do dowolnego elementu. Podobnie obiekt rzutowanie typu nie jest dopuszczalne l wartością, więc żadnego przypisania nie jest możliwe do obiektu rzutowanie typu.

**Microsoft Specific**

Rzutowanie typu może być wyrażeniem l wartością, tak długo, jak rozmiar identyfikatora nie zmienia się. Aby uzyskać informacji na temat wyrażeniem l-wartości, zobacz [wyrażenia wartości L i r](../c-language/l-value-and-r-value-expressions.md).

**END specyficzny dla Microsoft**

Można przekonwertować wyrażenia na typ `void` z rzutowania, ale wyrażenie wynikowe mogą być używane tylko wtedy, gdy wartość nie jest wymagane. Wskaźnik do obiektu jest konwertowana na **void** <strong>\*</strong> i powrót do oryginalnego typu powróci do oryginalnej wartości.

## <a name="see-also"></a>Zobacz też

[Konwersje typów](../c-language/type-conversions-c.md)