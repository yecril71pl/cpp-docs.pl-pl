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
ms.openlocfilehash: cc2b6d87d6fedf8d36373c901cdb6a6ba8b5f0e7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231458"
---
# <a name="type-cast-conversions"></a>Konwersje rzutowania typów

Możesz użyć rzutowania typu, aby jawnie skonwertować typy.

**Składnia**

*wyrażenie cast*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie jednoargumentowe*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie cast* **(***type-name***)**      

*Nazwa typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specyfikator-kwalifikator list* *abstract-deklarator*<sub>opt</sub>

*Nazwa typu* jest typem i *wyrażeniem Cast* jest wartością, która ma zostać przekonwertowana na ten typ. Wyrażenie, którego typem jest rzutowanie, nie jest wartością l. *Wyrażenie cast* jest konwertowane tak, jakby było przypisane do zmiennej typu Type *-name*. Reguły konwersji dla przypisań (opisane w [konwersji przypisania](../c-language/assignment-conversions.md)) dotyczą także rzutowania typu. W poniższej tabeli przedstawiono typy, które mogą być rzutowane na dowolny dany typ.

### <a name="legal-type-casts"></a>Rzutowania typu prawnego

|Typy docelowe|Potencjalne źródła|
|-----------------------|-----------------------|
|Typy całkowite|Dowolny typ całkowity lub typ zmiennoprzecinkowy lub wskaźnik do obiektu|
|Liczba zmiennoprzecinkowa|Dowolny typ arytmetyczny|
|Wskaźnik do obiektu lub ( **`void`** <strong>\*</strong> )|Dowolny typ Integer, ( **`void`** <strong>\*</strong> ), wskaźnik do obiektu lub wskaźnik funkcji|
|Wskaźnik funkcji|Dowolny typ całkowity, wskaźnik do obiektu lub wskaźnik funkcji|
|Struktura, Unia lub tablica|Brak|
|Typ void|Dowolny typ|

Dowolny identyfikator może być rzutowany na **`void`** Typ. Jeśli jednak typ określony w wyrażeniu Cast Type nie jest **`void`** , to identyfikator, który jest rzutowany na ten typ, nie może być **`void`** wyrażeniem. Każde wyrażenie może być rzutowane na **`void`** , ale wyrażenie typu **`void`** nie może być rzutowane na jakikolwiek inny typ. Na przykład funkcja z **`void`** typem zwracanym nie może mieć jego rzutowania Return na inny typ.

Należy zauważyć, że **`void`** <strong>\*</strong> wyrażenie ma wskaźnik typu do **`void`** , nie typ **`void`** . Jeśli obiekt jest rzutowany na **`void`** Typ, wyrażenie wyniki nie może zostać przypisane do żadnego elementu. Podobnie obiekt rzutowania typu nie jest akceptowalną wartością l, więc nie można wykonać przypisania do obiektu rzutowania typu.

**Specyficzne dla firmy Microsoft**

Rzutowanie typu może być wyrażeniem l-wartości, o ile rozmiar identyfikatora nie zmienia się. Aby uzyskać informacje o wyrażeniach l-wartościowych, zobacz [l-Value i R-Value Expressions](../c-language/l-value-and-r-value-expressions.md).

**ZAKOŃCZENIE określonych przez firmę Microsoft**

Można przekonwertować wyrażenie na typ **`void`** za pomocą rzutowania, ale wyrażenie wyniku może być używane tylko wtedy, gdy wartość nie jest wymagana. Wskaźnik obiektu konwertowany do **`void`** <strong>\*</strong> i z powrotem do oryginalnego typu zwróci pierwotną wartość.

## <a name="see-also"></a>Zobacz także

[Konwersje typów](../c-language/type-conversions-c.md)
