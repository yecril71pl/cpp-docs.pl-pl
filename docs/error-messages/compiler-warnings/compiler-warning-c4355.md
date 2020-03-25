---
title: Ostrzeżenie kompilatora C4355
ms.date: 11/04/2016
f1_keywords:
- C4355
helpviewer_keywords:
- C4355
ms.assetid: b819ecab-8a07-42d7-8fa4-1180d51626c0
ms.openlocfilehash: ddc0d1968ae373ff1e81c98a513e6f84fdb885e1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165330"
---
# <a name="compiler-warning-c4355"></a>Ostrzeżenie kompilatora C4355

'this': używany na liście inicjatora bazowego elementu członkowskiego

**Ten** wskaźnik jest prawidłowy tylko wewnątrz niestatycznych funkcji składowych. Nie można jej użyć na liście inicjatorów dla klasy bazowej.

Konstruktory klasy podstawowej i konstruktory elementów członkowskich klasy są wywoływane przed **tym** konstruktorem. W efekcie przeszedł wskaźnik do niekonstruowanego obiektu do innego konstruktora. Jeśli te inne konstruktory uzyskują dostęp do dowolnych elementów członkowskich lub wywołują funkcje składowe, wynik będzie niezdefiniowany. Nie należy używać **tego** wskaźnika, dopóki cała konstrukcja nie zostanie ukończona.

To ostrzeżenie jest domyślnie wyłączone. Aby uzyskać więcej informacji [, zobacz ostrzeżenia kompilatora, które są domyślnie wyłączone](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

Poniższy przykład generuje C4355:

```cpp
// C4355.cpp
// compile with: /w14355 /c
#include <tchar.h>

class CDerived;
class CBase {
public:
   CBase(CDerived *derived): m_pDerived(derived) {};
   ~CBase();
   virtual void function() = 0;

   CDerived * m_pDerived;
};

class CDerived : public CBase {
public:
   CDerived() : CBase(this) {};   // C4355 "this" used in derived c'tor
   virtual void function() {};
};

CBase::~CBase() {
   m_pDerived -> function();
}

int main() {
   CDerived myDerived;
}
```
