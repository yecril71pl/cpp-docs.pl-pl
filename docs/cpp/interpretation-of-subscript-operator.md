---
title: Interpretacja operatora indeksu dolnego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- subscript operator [C++], interpretation of
- arrays [C++], subscripting
- interpreting subscript operators [C++]
- operators [C++], interpretation of subscript
ms.assetid: 8852ca18-9d5b-43f7-b8bd-abc89364fbf2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75659730198e09a172625c54bfcbdd54b7a9f857
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404791"
---
# <a name="interpretation-of-subscript-operator"></a>Interpretacja operatora indeksu dolnego
Inne operatory operator indeksu dolnego, takich jak (**[**) mogą ponownie zdefiniowana przez użytkownika. Domyślne zachowanie operatora indeksu dolnego, jeżeli nie jest przeciążona, to aby połączyć nazwę tablicy i indeks dolny przy użyciu następującej metody:  
  
 \*((*nazwa macierzy*) + (*indeks dolny*))  
  
 Jak dodanie wszystkich obejmuje typy wskaźników skalowanie jest wykonywane automatycznie Aby dostosować rozmiar tego typu. W związku z tym, wynikowa wartość nie jest *indeks dolny* bajtów z pochodzenia *nazwa macierzy*; zamiast jest *indeks dolny*th elementu tablicy. (Aby uzyskać więcej informacji na temat tej konwersji, zobacz [operatory addytywne](../cpp/additive-operators-plus-and.md).)  
  
 Podobnie dla tablic wielowymiarowych adres jest tworzony przy użyciu następującej metody:  
  
 **((**   
 ***Nazwa tablicy* ) + ()**   
 ***Indeks dolny* 1***max*2  *\* max*3 *.. opisanej*n) **+** *indeks dolny*2  *\* max*3 *.. opisanej*n).   . . *+* *Indeks dolny*n))  
  
## <a name="see-also"></a>Zobacz także  
 [Tablice](../cpp/arrays-cpp.md)