---
title: Ostrzeżenie kompilatora C4355 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4355
dev_langs:
- C++
helpviewer_keywords:
- C4355
ms.assetid: b819ecab-8a07-42d7-8fa4-1180d51626c0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 44833c8e640002f2f94d44938641fa3c1fa33db7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46115310"
---
# <a name="compiler-warning-c4355"></a>Ostrzeżenie kompilatora C4355

'this': używany na liście inicjatora bazowego elementu członkowskiego

**To** wskaźnik jest prawidłowy tylko w obrębie Niestatyczne funkcje Członkowskie. Nie można użyć na liście inicjatora dla klasy bazowej.

Konstruktory klasy bazowej i konstruktory składowej klasy, które są wywoływane przed **to** konstruktora. W efekcie zrealizowaniu wskaźnik do obiektu unconstructed do innego konstruktora. Jeśli te inne konstruktory dostęp do wszystkich członków lub wywoływać funkcje Członkowskie na tym, wynik jest niezdefiniowana. Nie należy używać **to** wskaźnika przed ukończeniem wszystkich konstrukcji.

To ostrzeżenie jest domyślnie wyłączona. Zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.

Poniższy przykład spowoduje wygenerowanie C4355:

```
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