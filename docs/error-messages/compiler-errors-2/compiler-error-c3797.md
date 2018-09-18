---
title: Błąd kompilatora C3797 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3797
dev_langs:
- C++
helpviewer_keywords:
- C3797
ms.assetid: ab27ff34-8c1d-4297-b004-9e39bd3a4f25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ac1ded1c95f7e8bea9598e468010c75d8bd917a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033423"
---
# <a name="compiler-error-c3797"></a>Błąd kompilatora C3797

"override": deklaracja zdarzenia nie może posiadać specyfikatora przesłonięcia (powinna być umieszczona dla metod dodawania/usuwania/podbicia zdarzeń zamiast)

Nie można zastąpić trivial zdarzeń (zdarzenia bez metody dostępu jawnie zdefiniowanych) z innym zdarzeniem prosta. Zdarzenie nadrzędne należy zdefiniować jego zachowanie za pomocą funkcji dostępu.

Aby uzyskać więcej informacji, zobacz [zdarzeń](../../windows/event-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3797.

```
// C3797.cpp
// compile with: /clr /c
delegate void MyDel();

ref class Class1 {
public:
   virtual event MyDel ^ E;
};

ref class Class2 : public Class1 {
public:
   virtual event MyDel ^ E override;   // C3797
};

// OK
ref class Class3 : public Class1 {
public:
   virtual event MyDel ^ E {
      void add(MyDel ^ d) override {}
      void remove(MyDel ^ d) override {}
   }
};
```