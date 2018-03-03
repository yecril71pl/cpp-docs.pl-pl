---
title: "Odejmowanie (–) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- operators [C], subtraction
- subtraction operator, syntax
ms.assetid: 9cacba7d-20b3-4372-8a63-ba5d8ee64177
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b32986513a94c20f0fb0cd1b4c65dd21e8c9e8aa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="subtraction--"></a>Odejmowania (-)
Operator odejmowania (**-**) odejmuje drugi argument od pierwszego. Oba argumenty mogą być typy całkowitą lub zmiennoprzecinkową lub jeden argument może być wskaźnik i inne liczbą całkowitą.  
  
 Po dwóch wskaźników są odejmować, różnica jest konwertowana na podpisem całkowitej wartości przez podzielenie różnicy przez rozmiar wartości typu który adres wskaźników. Rozmiar całkowitą wartość jest definiowana za pomocą typu **ptrdiff_t —** w standardowych dołączanych plików STDDEF. H. Wynik reprezentuje liczbę pozycji pamięci między dwoma adresami tego typu. Wynik jest tylko gwarancji zrozumiały dla dwa elementy o tej samej tablicy, zgodnie z opisem w [arytmetyki wskaźnika](../c-language/pointer-arithmetic.md).  
  
 Jeśli wartość jest odejmowana od wartości wskaźnika, operator odejmowania konwertuje wartość całkowita (*i*) mnożąc przez rozmiar wartość, która dotyczy wskaźnika. Po przeprowadzeniu konwersji, wartość całkowita reprezentuje *i* pozycji pamięci, gdzie każda pozycja ma długości określonej przez typ wskaźnika. W przypadku przekonwertowanego całkowita jest odejmowany od wartości wskaźnika, wynik jest adresem pamięci *i* pozycji przed oryginalnego adresu. Wskaźnik nowych punktów do wartości typu opisany w oryginalnej wartości wskaźnika.  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory dodawania języka C](../c-language/c-additive-operators.md)