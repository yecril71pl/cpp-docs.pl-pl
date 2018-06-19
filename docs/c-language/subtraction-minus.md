---
title: Odejmowanie (–) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C], subtraction
- subtraction operator, syntax
ms.assetid: 9cacba7d-20b3-4372-8a63-ba5d8ee64177
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 295c6bc33b42ed34fd476dbc72bec9dd398efa14
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32386949"
---
# <a name="subtraction--"></a>Odejmowania (-)
Operator odejmowania (**-**) odejmuje drugi argument od pierwszego. Oba argumenty mogą być typy całkowitą lub zmiennoprzecinkową lub jeden argument może być wskaźnik i inne liczbą całkowitą.  
  
 Po dwóch wskaźników są odejmować, różnica jest konwertowana na podpisem całkowitej wartości przez podzielenie różnicy przez rozmiar wartości typu który adres wskaźników. Rozmiar całkowitą wartość jest definiowana za pomocą typu **ptrdiff_t —** w standardowych dołączanych plików STDDEF. H. Wynik reprezentuje liczbę pozycji pamięci między dwoma adresami tego typu. Wynik jest tylko gwarancji zrozumiały dla dwa elementy o tej samej tablicy, zgodnie z opisem w [arytmetyki wskaźnika](../c-language/pointer-arithmetic.md).  
  
 Jeśli wartość jest odejmowana od wartości wskaźnika, operator odejmowania konwertuje wartość całkowita (*i*) mnożąc przez rozmiar wartość, która dotyczy wskaźnika. Po przeprowadzeniu konwersji, wartość całkowita reprezentuje *i* pozycji pamięci, gdzie każda pozycja ma długości określonej przez typ wskaźnika. W przypadku przekonwertowanego całkowita jest odejmowany od wartości wskaźnika, wynik jest adresem pamięci *i* pozycji przed oryginalnego adresu. Wskaźnik nowych punktów do wartości typu opisany w oryginalnej wartości wskaźnika.  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory dodawania języka C](../c-language/c-additive-operators.md)