---
title: Wyrażenia wartości L i R
ms.date: 11/04/2016
helpviewer_keywords:
- L-values
- member-selection expressions
- R-value expressions
- subscript expressions
ms.assetid: b790303e-ec6f-4d0d-bc55-df42da267172
ms.openlocfilehash: 0c287c45f2d7ea121c9c706b3b761ff7ce6ec232
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87199831"
---
# <a name="l-value-and-r-value-expressions"></a>Wyrażenia wartości L i R

Wyrażenia, które odwołują się do lokalizacji pamięci są nazywane wyrażeniami „l-wartości”. L-wartość reprezentuje wartość "lokalizatora" regionu magazynu lub wartość "Left", co oznacza, że może pojawić się po lewej stronie znaku równości ( **=** ). L-wartości są często identyfikatorami.

Wyrażenia odnoszące się do lokalizacji, którą można modyfikować, nazywamy „l-wartościami, które można modyfikować”. Niemodyfikowalna wartość l nie może mieć typu tablicy, niekompletnego typu ani typu z **`const`** atrybutem. Dla struktur i Unii, aby można było modyfikować l-wartości, nie mogą mieć żadnych składowych z **`const`** atrybutem. Nazwa identyfikatora oznacza lokalizację pamięci, podczas gdy wartość zmiennej jest wartością przechowywaną w tej lokalizacji.

Identyfikator jest l-wartością, którą można modyfikować, jeśli dotyczy lokalizacji w pamięci i jeśli jego typem jest typ arytmetyczny, struktura, unia lub wskaźnik. Na przykład, jeśli `ptr` jest wskaźnikiem do regionu pamięci, `*ptr` jest modyfikowalną l-wartością, która określa region pamięci wskazywany przez `ptr`.

Każde z następujących wyrażeń C może być wyrażeniem l-wartości:

- Identyfikator typu całkowitego, zmiennoprzecinkowego, wskaźnika, struktury lub unii

- Wyrażenie indeksu dolnego (**[]**), które nie jest szacowane do tablicy

- Wyrażenie wyboru elementu członkowskiego ( **->** lub **.**)

- Wyrażenie jednoargumentowe ( <strong>\*</strong> ), które nie odwołuje się do tablicy

- Wyrażenie l-wartości w nawiasach

- **`const`** Obiekt (l-wartość niemodyfikowalną)

„R-wartość” jest czasami używana do opisywania wartości wyrażenia i odróżniania jej od l-wartości. Wszystkie l-wartości są r-wartościami, ale nie wszystkie r-wartości są l-wartościami.

**Specyficzne dla firmy Microsoft**

Język Microsoft C zawiera rozszerzenie standardu ANSI C, które umożliwia rzutowanie l-wartości, aby móc używać ich jako l-wartości, tak długo, jak rozmiar obiektu nie jest zwiększany poprzez rzutowanie. (Zobacz [Konwersje rzutowania typów](../c-language/type-cast-conversions.md) , aby uzyskać więcej informacji.) Poniższy przykład ilustruje tę funkcję:

```
char *p ;
short  i;
long l;

(long *) p = &l ;       /* Legal cast   */
(long) i = l ;          /* Illegal cast */
```

Domyślnym ustawieniem dla Microsoft C jest włączenie rozszerzeń Microsoft. Aby wyłączyć te rozszerzenia, użyj opcji kompilatora/za.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Operandy i wyrażenia](../c-language/operands-and-expressions.md)
