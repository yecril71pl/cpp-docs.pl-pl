---
title: Ostrzeżenie kompilatora (poziom 1) C4621
ms.date: 11/04/2016
f1_keywords:
- C4621
helpviewer_keywords:
- C4621
ms.assetid: 40931bd9-cb89-497e-86f0-cec9f016c63c
ms.openlocfilehash: a48934fd097f9039988db32511ca87cbd66b22d2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199757"
---
# <a name="compiler-warning-level-1-c4621"></a>Ostrzeżenie kompilatora (poziom 1) C4621

nie znaleziono przyrostkowej formy "operator--" dla typu "Type", przy użyciu formy prefiksu

Dla danego typu nie zdefiniowano operatora zmniejszania przyrostu. Kompilator użył operatora przeciążonego prefiksu.

To ostrzeżenie można uniknąć, definiując Przyrostkowy operator `--`. Utwórz dwuargumentową wersję operatora `--`, jak pokazano poniżej:

```cpp
// C4621.cpp
// compile with: /W1
class A
{
public:
   A(int nData) : m_nData(nData)
   {
   }

   A operator--()
   {
      m_nData -= 1;
      return *this;
   }

   // A operator--(int)
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
   --a;
   a--;   // C4621
}
```
