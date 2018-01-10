---
title: void (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: void_cpp
dev_langs: C++
helpviewer_keywords:
- void keyword [C++]
- functions [C++], void
- pointers, void
ms.assetid: d203edba-38e6-4056-8b89-011437351057
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a800aca290a178e3b193c245df515385311b5593
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="void-c"></a>void (C++)
Gdy jest używany jako typ zwracany funkcji, `void` — słowo kluczowe Określa, że funkcja nie zwraca wartości. Gdy jest używany dla listy wartości parametru funkcji void określa funkcja nie przyjmuje żadnych parametrów. Gdy jest używany w deklaracji wskaźnika, void Określa, że wskaźnik "uniwersalne".  
  
 Jeśli typ wskaźnika jest **void \*** , wskaźnik może wskazywać żadnych zmiennej, która nie jest zadeklarowany z **const** lub `volatile` — słowo kluczowe. Nie można usunąć odwołania wskaźnika typu void, chyba że jest rzutowane do innego typu. Wskaźnik void może zostać przekonwertowany do żadnego innego typu wskaźnika danych.  
  
 Wskazać void wskaźnika do funkcji, ale nie do elementu członkowskiego klasy w języku C++.  
  
 Nie można zadeklarować zmiennej typu void.  
  
## <a name="example"></a>Przykład  
  
```  
// void.cpp  
void vobject;   // C2182  
void *pv;   // okay  
int *pint; int i;  
int main() {  
   pv = &i;  
   // Cast optional in C required in C++  
   pint = (int *)pv;  
}   
```  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe](../cpp/keywords-cpp.md)   
 [Typy podstawowe](../cpp/fundamental-types-cpp.md)