---
title: Kompilatora (poziom 1) ostrzeżenie C4620 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4620
dev_langs:
- C++
helpviewer_keywords:
- C4620
ms.assetid: fed29934-b797-47e8-bbea-c7e5f8dd6e93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bdd192ad130a1a1cc1aa96bd8e423b01554b0720
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279507"
---
# <a name="compiler-warning-level-1-c4620"></a>Kompilator C4620 ostrzegawcze (poziom 1)
nie przyrostkowej formy "operator ++" znaleziono dla typu "type", użyta zostanie forma przedrostkowa  
  
 Nie istnieje żaden operator inkrementacji przyrostek zdefiniowane dla danego typu. Kompilator używany operator przeciążone prefiks.  
  
 To ostrzeżenie można uniknąć, definiując przyrostek `++` operatora. Utwórz wersję dwuargumentowej `++` operatora, jak pokazano poniżej:  
  
```  
// C4620.cpp  
// compile with: /W1  
class A  
{  
public:  
   A(int nData) : m_nData(nData)  
   {  
   }  
  
   A operator++()  
   {  
      m_nData -= 1;  
      return *this;  
   }  
  
   // A operator++(int)  
   // {  
   //    A tmp = *this;  
   //    m_nData -= 1;  
   //    return tmp;  
   // }  
  
private:  
   int m_nData;  
};  
  
int main()  
{  
   A a(10);  
   ++a;  
   a++;   // C4620  
}  
```