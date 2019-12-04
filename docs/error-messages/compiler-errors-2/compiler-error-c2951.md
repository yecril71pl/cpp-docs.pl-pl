---
title: Błąd kompilatora C2951
ms.date: 11/04/2016
f1_keywords:
- C2951
helpviewer_keywords:
- C2951
ms.assetid: c6f95aa2-c894-425b-a51c-d40d70c8daa1
ms.openlocfilehash: fdb837f8e9a9b769d470b70b962ce63d144161e1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755983"
---
# <a name="compiler-error-c2951"></a>Błąd kompilatora C2951

Deklaracje typów są dozwolone tylko w globalnym, przestrzeni nazw lub zakresie klasy

Nie można zadeklarować klasy generycznej lub szablonu poza zakresem globalnym lub przestrzeni nazw. W przypadku stosowania deklaracji ogólnych lub szablonów w pliku dołączanym upewnij się, że plik dołączany jest w zakresie globalnym.

Poniższy przykład generuje C2951:

```cpp
// C2951.cpp
template <class T>
class A {};

int main() {
   template <class T>   // C2951
   class B {};
}
```

C2951 może również wystąpić przy użyciu typów ogólnych:

```cpp
// C2951b.cpp
// compile with: /clr /c

// OK
generic <class T>
ref class GC { };

int main() {
   generic <class T> ref class GC2 {};   // C2951
}
```
