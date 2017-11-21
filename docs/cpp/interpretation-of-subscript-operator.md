---
title: Interpretacja operatora indeksu dolnego | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- subscript operator [C++], interpretation of
- arrays [C++], subscripting
- interpreting subscript operators [C++]
- operators [C++], interpretation of subscript
ms.assetid: 8852ca18-9d5b-43f7-b8bd-abc89364fbf2
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fcd376a5322c525c59b2423bd59507699f0a7c4c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="interpretation-of-subscript-operator"></a>Interpretacja operatora indeksu dolnego
Jak innymi operatorami operator indeksu dolnego (**[**) można ponownie zdefiniować przez użytkownika. Domyślnym zachowaniem operatora indeksu dolnego, jeśli nie jest przeciążona, jest łączenie nazwa tablicy i indeks przy użyciu następujących metod:  
  
 \*((*nazwa tablicy*) + (*indeks dolny*))  
  
 Jak dodanie wszystkich typów wskaźnikowych obejmuje skalowanie jest realizowane automatycznie dostosowanie rozmiaru tego typu. W związku z tym wynikowe wartość nie jest *indeks dolny* bajtów z pochodzenia *nazwa tablicy*; zamiast jest *indeks dolny*element th tablicy. (Aby uzyskać więcej informacji na temat tej konwersji, zobacz [operatory dodatku](../cpp/additive-operators-plus-and.md).)  
  
 Podobnie dla tablic wielowymiarowych adres jest uzyskiwany przy użyciu następujących metod:  
  
 **((**   
 ***Nazwa tablicy* ) + ()**   
 ***Indeks dolny* 1***max*2  *\* max*3*.. opisanej*n)  **+**  *indeks dolny*2  *\* max*3*.. opisanej*n).   . . *+**indeks dolny*n))  
  
## <a name="see-also"></a>Zobacz też  
 [Tablice](../cpp/arrays-cpp.md)