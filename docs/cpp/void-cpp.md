---
title: void (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- void_cpp
dev_langs:
- C++
helpviewer_keywords:
- void keyword [C++]
- functions [C++], void
- pointers, void
ms.assetid: d203edba-38e6-4056-8b89-011437351057
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dbb46302c2ae8834ab9a2a626a3bfb77c41996a2
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461481"
---
# <a name="void-c"></a>void (C++)
Gdy jest używana jako zwracany typ funkcji, **void** — słowo kluczowe Określa, że funkcja nie zwraca wartości. Gdy jest używana dla listy wartości parametru funkcji void Określa, że funkcja nie przyjmuje żadnych parametrów. W przypadku użycia w deklaracji wskaźnika, typ void Określa, że wskaźnik "uniwersalne".  
  
 Jeśli typ wskaźnika `void *`, wskaźnik może wskazywać jakakolwiek zmienna, która nie jest zadeklarowana za pomocą **const** lub **volatile** — słowo kluczowe. Nie można usunąć odwołania wskaźnika void, chyba że jest rzutowane do innego typu. Dowolny inny typ wskaźnika danych, można przekonwertować na wskaźnik typu void.  
  
 Pusty wskaźnik może wskazywać na funkcję, ale nie do składowej klasy w języku C++.  
  
 Nie można zadeklarować zmienną typu void.  
  
## <a name="example"></a>Przykład  
  
```cpp 
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
  
## <a name="see-also"></a>Zobacz także  
 [Keywords](../cpp/keywords-cpp.md)   
 [Typy podstawowe](../cpp/fundamental-types-cpp.md)