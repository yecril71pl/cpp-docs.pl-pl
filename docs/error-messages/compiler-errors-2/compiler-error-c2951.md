---
title: Błąd kompilatora C2951
ms.date: 11/04/2016
f1_keywords:
- C2951
helpviewer_keywords:
- C2951
ms.assetid: c6f95aa2-c894-425b-a51c-d40d70c8daa1
ms.openlocfilehash: dbc7186edfce6cc12a38fb2fc1dda08ac4a181c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300729"
---
# <a name="compiler-error-c2951"></a>Błąd kompilatora C2951

deklaracje typu są dozwolone tylko w globalnym, przestrzeni nazw lub zakresie klasy

Nie można zadeklarować ogólny lub klasą szablonu poza globalne lub zakresie przestrzeni nazw. Po wprowadzeniu swojej deklaracji generyczny lub szablonu w pliku dołączanego, upewnij się, że pliku dyrektywy include jest w zakresie globalnym.

Poniższy przykład spowoduje wygenerowanie C2951:

```
// C2951.cpp
template <class T>
class A {};

int main() {
   template <class T>   // C2951
   class B {};
}
```

C2951 może również wystąpić, gdy za pomocą typów ogólnych:

```
// C2951b.cpp
// compile with: /clr /c

// OK
generic <class T>
ref class GC { };

int main() {
   generic <class T> ref class GC2 {};   // C2951
}
```