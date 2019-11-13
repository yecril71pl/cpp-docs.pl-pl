---
title: Ostrzeżenie kompilatora (poziom 1) C4620
ms.date: 11/04/2016
f1_keywords:
- C4620
helpviewer_keywords:
- C4620
ms.assetid: fed29934-b797-47e8-bbea-c7e5f8dd6e93
ms.openlocfilehash: d03c7d845923b918fbb665933147d8ff97cda7ab
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051467"
---
# <a name="compiler-warning-level-1-c4620"></a>Ostrzeżenie kompilatora (poziom 1) C4620

nie znaleziono przyrostkowej formy "operator + +" dla typu "Type", przy użyciu formy prefiksu

Nie istnieje żaden Przyrostkowy operator przyrostu zdefiniowany dla danego typu. Kompilator użył operatora przeciążonego prefiksu.

To ostrzeżenie można uniknąć, definiując Przyrostkowy operator `++`. Utwórz dwuargumentową wersję operatora `++`, jak pokazano poniżej:

```cpp
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