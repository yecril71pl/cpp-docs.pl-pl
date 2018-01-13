---
title: "Konwersje rzutowania typów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- data type conversion [C++], type-cast conversions
- conversions [C++], type-cast
- type casts
- explicit type conversions
- type casts [C++], about type-cast conversion
- type-cast conversions [C++]
ms.assetid: 57ab5902-f12f-4326-a2f6-6282f1d4025a
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f402eb49e86c8d6d3ce6c332172375125f577a2b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="type-cast-conversions"></a>Konwersje rzutowania typów
Rzutowania typów umożliwia jawnej konwersji typów.  
  
 **Składnia**  
  
 *wyrażenie CAST*:  
 *wyrażenie jednoargumentowe*  
  
 **(***nazwy typu***)***wyrażenie cast*   
  
 *Nazwa typu*:  
 *Specyfikator kwalifikator listy abstrakcyjny — deklarator* opcjonalnych  
  
 *Nazwy typu* jest typem i *wyrażenie cast* jest wartość ma zostać przekonwertowane na tego typu. Wyrażenia z rzutowanie typu nie jest wartością l-value. *Wyrażenie cast* przekonwertowaniu tak, jakby była został przypisany do zmiennej typu *nazwy typu*. Reguły konwersji dla przypisania (opisane w temacie [konwersje przypisań](../c-language/assignment-conversions.md)) dotyczą również rzutowania typu. W poniższej tabeli przedstawiono typy, które mogą być rzutowane do danego typu.  
  
### <a name="legal-type-casts"></a>Rzutowania typów prawnych  
  
|Typy docelowego|Potencjalne źródła|  
|-----------------------|-----------------------|  
|Typy całkowite|Dowolnego typu Liczba całkowita lub typ zmiennoprzecinkowy lub wskaźnika do obiektu|  
|Zmiennoprzecinkowe|Dowolny typ arytmetyczny|  
|Wskaźnik do obiektu lub (**void \*** )|Dowolnego typu Liczba całkowita (**void \*** ), wskaźnika do obiektu lub wskaźnik funkcji|  
|wskaźnik funkcji|Dowolnego typu całkowitego, wskaźnik do obiektu lub wskaźnik funkcji|  
|Struktura, Unią lub tablicy|Brak|  
|Typ void|Dowolnego typu|  
  
 Wszelkie identyfikator mogą być rzutowane na `void` typu. Jeśli typ określony w wyrażeniu rzutowanie typu nie jest jednak `void`, a następnie jest identyfikator rzutować czy typ nie może być `void` wyrażenia. Dowolne wyrażenie mogą być rzutowane na `void`, ale wyrażenie typu `void` nie można rzutować na innego typu. Na przykład funkcja z `void` zwracany typ nie może mieć jego powrotu rzutowanie do innego typu.  
  
 Należy pamiętać, że **void \***  wyrażenie zawiera typ wskaźnika do `void`, nie jest typu `void`. Jeśli obiekt jest rzutowane na `void` typu, wynikowe wyrażenie nie można przypisać do dowolnego elementu. Podobnie obiekt rzutowanie typu nie jest dopuszczalne wartości l, więc nie przypisanie nie jest możliwe do obiektu rzutowanie typu.  
  
 **Dotyczące firmy Microsoft**  
  
 Rzutowanie typu może być wyrażenia wartości l, dopóki nie zmienia rozmiar identyfikatora. Aby uzyskać informacje na wyrażenia wartości l, zobacz [wartości L i r wyrażenia](../c-language/l-value-and-r-value-expressions.md).  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
 Można przekonwertować na typ wyrażenia `void` z rzutowanie, ale wynikowe wyrażenie może być używana tylko wtedy, gdy wartość nie jest wymagane. Wskaźnik do obiektu przekonwertować **void \***  i wstecz do oryginalnego typu powróci do oryginalnej wartości.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersje typów](../c-language/type-conversions-c.md)