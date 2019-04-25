---
title: Wyrażenia wartości L i R
ms.date: 11/04/2016
helpviewer_keywords:
- L-values
- member-selection expressions
- R-value expressions
- subscript expressions
ms.assetid: b790303e-ec6f-4d0d-bc55-df42da267172
ms.openlocfilehash: bd5f702588a11b7841f77de539d113206833cde9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325523"
---
# <a name="l-value-and-r-value-expressions"></a>Wyrażenia wartości L i R

Wyrażenia, które odwołują się do lokalizacji pamięci są nazywane wyrażeniami „l-wartości”. L wartość reprezentuje wartość "lokatora" obszaru magazynowania lub "lewej" wartości, co oznacza, że może występować po lewej stronie znaku równości (**=**). L-wartości są często identyfikatorami.

Wyrażenia odnoszące się do lokalizacji, którą można modyfikować, nazywamy „l-wartościami, które można modyfikować”. Modyfikowalną l wartością nie może mieć typu tablicowego, typu niekompletnego lub typu z **const** atrybutu. Dla struktur i Unii to modyfikowalnych l wartościami, nie mogą posiadać żadnych elementów członkowskich z **const** atrybutu. Nazwa identyfikatora oznacza lokalizację pamięci, podczas gdy wartość zmiennej jest wartością przechowywaną w tej lokalizacji.

Identyfikator jest l-wartością, którą można modyfikować, jeśli dotyczy lokalizacji w pamięci i jeśli jego typem jest typ arytmetyczny, struktura, unia lub wskaźnik. Na przykład, jeśli `ptr` jest wskaźnikiem do regionu pamięci, `*ptr` jest modyfikowalną l-wartością, która określa region pamięci wskazywany przez `ptr`.

Każde z następujących wyrażeń C może być wyrażeniem l-wartości:

- Identyfikator typu całkowitego, zmiennoprzecinkowego, wskaźnika, struktury lub unii

- Indeks dolny (**[**) wyrażenie, które nie jest obliczone do tablicy

- Wyrażenie wyboru elementów członkowskich (**->** lub **.**)

- Jednoargumentowe (<strong>\*</strong>) wyrażenie, które nie odwołuje się do tablicy

- Wyrażenie l-wartości w nawiasach

- A **const** obiektu (niemodyfikowalnymi l wartość)

„R-wartość” jest czasami używana do opisywania wartości wyrażenia i odróżniania jej od l-wartości. Wszystkie l-wartości są r-wartościami, ale nie wszystkie r-wartości są l-wartościami.

**Microsoft Specific**

Język Microsoft C zawiera rozszerzenie standardu ANSI C, które umożliwia rzutowanie l-wartości, aby móc używać ich jako l-wartości, tak długo, jak rozmiar obiektu nie jest zwiększany poprzez rzutowanie. (Zobacz [konwersje rzutowania typów](../c-language/type-cast-conversions.md) Aby uzyskać więcej informacji.) Poniższy przykład ilustruje tę cechę:

```
char *p ;
short  i;
long l;

(long *) p = &l ;       /* Legal cast   */
(long) i = l ;          /* Illegal cast */
```

Wartość domyślna Microsoft C to, że są włączone rozszerzenia Microsoft. Aby wyłączyć te rozszerzenia, należy użyć /Za — opcja kompilatora.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Operandy i wyrażenia](../c-language/operands-and-expressions.md)
