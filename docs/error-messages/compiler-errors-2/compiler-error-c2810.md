---
title: Błąd kompilatora C2810
ms.date: 11/04/2016
f1_keywords:
- C2810
helpviewer_keywords:
- C2810
ms.assetid: f63e8f24-d7f6-42ac-904f-72ff49592ba6
ms.openlocfilehash: 2c598065fb6d5965f92504019275a921d12acb27
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760585"
---
# <a name="compiler-error-c2810"></a>Błąd kompilatora C2810

"Interface": interfejs może dziedziczyć tylko po innym interfejsie

[Interfejs](../../cpp/interface.md) może dziedziczyć tylko po innym interfejsie i może nie dziedziczyć z klasy lub struktury.

Poniższy przykład generuje C2810:

```cpp
// C2810.cpp
#include <unknwn.h>
class CBase1 {
public:
  HRESULT mf1();
  int  m_i;
};

[object, uuid="40719E20-EF37-11D1-978D-0000F805D73B"]
__interface IDerived : public CBase1 {  // C2810
// try the following line instead
// __interface IDerived {
   HRESULT mf2(void *a);
};

struct CBase2 {
   HRESULT mf1(int a, char *b);
   HRESULT mf2();
};
```
