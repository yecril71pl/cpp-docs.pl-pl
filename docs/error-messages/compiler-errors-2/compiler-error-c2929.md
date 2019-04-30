---
title: Błąd kompilatora C2929
ms.date: 11/04/2016
f1_keywords:
- C2929
helpviewer_keywords:
- C2929
ms.assetid: 11134027-6adc-4733-b6bd-b94486bd1933
ms.openlocfilehash: fe2a56f7722c70c11e980fb6ee59230ffd056c5f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385722"
---
# <a name="compiler-error-c2929"></a>Błąd kompilatora C2929

'Identyfikator': jawne utworzenie wystąpień; Nie można jawnie wymusić i ograniczyć utworzenia wystąpienia składowej klasy szablonu

Nie można jawnie utworzyć wystąpienia identyfikatora podczas uniemożliwiające jego wystąpienia.

Poniższy przykład spowoduje wygenerowanie C2929:

```
// C2929.cpp
// compile with: /c
template<typename T>
class A {
public:
   A() {}
};

template A<int>::A();

extern template A<int>::A();   // C2929
```