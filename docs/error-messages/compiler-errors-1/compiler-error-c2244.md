---
title: Błąd kompilatora C2244
ms.date: 11/04/2016
f1_keywords:
- C2244
helpviewer_keywords:
- C2244
ms.assetid: d9911c12-ceb5-4f93-ac47-b44a485215c2
ms.openlocfilehash: 7cfa0cd7ff4290ca5f07fb712bbcac7dabf55f29
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615206"
---
# <a name="compiler-error-c2244"></a>Błąd kompilatora C2244

'Identyfikator': nie można dopasować definicji funkcji do istniejącej deklaracji

Nietypowe użycie operatora jednoargumentowego + był używany przed wywołaniem funkcji, które nie mają nawiasu.

Ten błąd występuje tylko w projektach C++.

Poniższy przykład spowoduje wygenerowanie C2244:

```
// C2244.cpp
int func(char) {
   return 0;
}

int func(int) {
   return 0;
}

int main() {
   +func;   // C2244
}
```

C2244 może również wystąpić, gdy Niepoprawna funkcja podpis ma być używany dla funkcji członkowskiej szablonu klasy.

```
// C2244b.cpp
// compile with: /c
template<class T>
class XYZ {
   void func(T t);
};

template<class T>
void XYZ<T>::func(int i) {}   // C2244 wrong function signature
// try the following line instead
// void XYZ<T>::func(T t) {}
```

C2244 może również wystąpić, gdy podpisu Niepoprawna funkcja jest używana do szablonem funkcji elementu członkowskiego.

```
// C2244c.cpp
// compile with: /c
class ABC {
   template<class T>
   void func(int i, T t);
};

template<class T>
void ABC::func(int i) {}   // C2244 wrong signature
// try the following line instead
// void ABC::func(int i, T t) {}
```

Częściowo nie można specjalizować szablonu funkcji.

```
// C2244d.cpp
template<class T, class U>
class QRS {
   void func(T t, U u);
};

template<class T>
void QRS<T,int>::func(T t, int u) {}   // C2244
```