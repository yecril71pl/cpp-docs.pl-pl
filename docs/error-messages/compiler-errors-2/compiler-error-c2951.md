---
title: Błąd kompilatora C2951 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2951
dev_langs:
- C++
helpviewer_keywords:
- C2951
ms.assetid: c6f95aa2-c894-425b-a51c-d40d70c8daa1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6757256f08c5c1ed0a35fbf1c2a70776a4f2936
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074672"
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