---
title: Błąd kompilatora C3227
ms.date: 11/04/2016
f1_keywords:
- C3227
helpviewer_keywords:
- C3227
ms.assetid: 7939c23a-96c8-43c2-89e9-f217d132d155
ms.openlocfilehash: 460000531dba77e42379199f276c9e2e02f43a9b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743422"
---
# <a name="compiler-error-c3227"></a>Błąd kompilatora C3227

"parameter": nie można użyć słowa kluczowego "Keyword" do przydzielenia typu ogólnego

Aby utworzyć wystąpienie typu, wymagany jest odpowiedni Konstruktor. Jednak kompilator nie jest w stanie zapewnić, że jest dostępny odpowiedni Konstruktor.

Aby rozwiązać ten problem, można użyć szablonów zamiast typów ogólnych lub użyć jednej z kilku metod tworzenia wystąpienia typu.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3227.

```cpp
// C3227.cpp
// compile with: /clr /c
generic<class T> interface class ICreate {
   static T Create();
};

generic <class T>
where T : ICreate<T>
ref class C {
   void f() {
      T t = new T;   // C3227

      // OK
      T t2 = ICreate<T>::Create();
      T t3 = safe_cast<T>( System::Activator::CreateInstance(T::typeid) );
   }
};
```
