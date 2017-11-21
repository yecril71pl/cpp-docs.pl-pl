---
title: "Wartości L i r wyrażeń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- L-values
- member-selection expressions
- R-value expressions
- subscript expressions
ms.assetid: b790303e-ec6f-4d0d-bc55-df42da267172
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8c2d37d95a20ac2a71c50d468a7793ae4ab8956f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="l-value-and-r-value-expressions"></a>Wyrażenia wartości L i R
Wyrażenia, które odwołują się do lokalizacji pamięci są nazywane wyrażeniami „l-wartości”. L wartość reprezentuje obszar magazynowania "lokalizatora" wartość lub wartość "lewo", co oznacza, że może występować na lewo od znaku równości (**=**). L-wartości są często identyfikatorami.  
  
 Wyrażenia odnoszące się do lokalizacji, którą można modyfikować, nazywamy „l-wartościami, które można modyfikować”. Modyfikowalną l wartość nie może mieć typu tablicy, niekompletnego typu lub typ z **const** atrybutu. Aby struktur i Unii być modyfikowalną l wartości, nie muszą mieć żadnych elementów członkowskich z **const** atrybutu. Nazwa identyfikatora oznacza lokalizację pamięci, podczas gdy wartość zmiennej jest wartością przechowywaną w tej lokalizacji.  
  
 Identyfikator jest l-wartością, którą można modyfikować, jeśli dotyczy lokalizacji w pamięci i jeśli jego typem jest typ arytmetyczny, struktura, unia lub wskaźnik. Na przykład, jeśli `ptr` jest wskaźnikiem do regionu pamięci, `*ptr` jest modyfikowalną l-wartością, która określa region pamięci wskazywany przez `ptr`.  
  
 Każde z następujących wyrażeń C może być wyrażeniem l-wartości:  
  
-   Identyfikator typu całkowitego, zmiennoprzecinkowego, wskaźnika, struktury lub unii  
  
-   Indeks dolny (**[**) wyrażenie, które nie może oszacować do tablicy  
  
-   Wyrażenia wyboru elementu członkowskiego ( **->**  lub **.**)  
  
-   Jednoargumentowy operator pośredni (**\***) wyrażenie odwołuje się do tablicy  
  
-   Wyrażenie l-wartości w nawiasach  
  
-   A **const** obiektu (niemodyfikowalnymi l wartość)  
  
 „R-wartość” jest czasami używana do opisywania wartości wyrażenia i odróżniania jej od l-wartości. Wszystkie l-wartości są r-wartościami, ale nie wszystkie r-wartości są l-wartościami.  
  
 **Dotyczące firmy Microsoft**  
  
 Język Microsoft C zawiera rozszerzenie standardu ANSI C, które umożliwia rzutowanie l-wartości, aby móc używać ich jako l-wartości, tak długo, jak rozmiar obiektu nie jest zwiększany poprzez rzutowanie. (Zobacz [konwersje rzutowania typów](../c-language/type-cast-conversions.md) Aby uzyskać więcej informacji.) Poniższy przykład ilustruje tę cechę:  
  
```  
char *p ;  
short  i;  
long l;  
  
(long *) p = &l ;       /* Legal cast   */  
(long) i = l ;          /* Illegal cast */  
```  
  
 Wartość domyślna Microsoft C to, czy są włączone rozszerzenia Microsoft. /Za — opcja kompilatora umożliwia wyłączenie tych rozszerzeń.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Operandy i wyrażenia](../c-language/operands-and-expressions.md)