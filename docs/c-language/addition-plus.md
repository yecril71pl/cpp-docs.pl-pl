---
title: Dodawania (+) | Dokumentacja firmy Microsoft
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
- pointers, adding integers
ms.assetid: b9014fee-825d-46ef-91db-5d46807081fc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d41fe0369235bbdaf6723d01fdaf4bbf552a9ea5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="addition-"></a>Dodawanie (+)
Operator dodawania (**+**) powoduje, że jego dwóch argumentów operacji do dodania. Oba argumenty mogą być typy całkowitą lub zmiennoprzecinkową lub jeden argument może być wskaźnik i inne liczbą całkowitą.  
  
 Po dodaniu całkowitą na wskaźnik, całkowita (*i*) jest konwertowana mnożąc przez rozmiar wartość, która dotyczy wskaźnika. Po przeprowadzeniu konwersji, wartość całkowita reprezentuje *i* pozycji pamięci, gdzie każda pozycja ma długości określonej przez typ wskaźnika. Woluminowi wartość całkowita przekonwertowana na wartość wskaźnika wynik jest dostępna nowa wartość wskaźnika, reprezentująca adres *i* pozycji z oryginalnego adresu. Nowa wartość wskaźnika adresów wartości tego samego typu, jak oryginalna wartość wskaźnika i dlatego jest taka sama jak indeksowanie tablicy (zobacz [tablice One-Dimensional](../c-language/one-dimensional-arrays.md) i [tablice wielowymiarowe](../c-language/multidimensional-arrays-c.md)). Jeśli suma wskaźnik wskazuje poza tablicy, z wyjątkiem w pierwszym lokalizacji poza górną granicę wynik jest niezdefiniowany. Aby uzyskać więcej informacji, zobacz [arytmetyki wskaźnika](../c-language/pointer-arithmetic.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory dodawania języka C](../c-language/c-additive-operators.md)