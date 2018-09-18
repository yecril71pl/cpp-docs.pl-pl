---
title: Błąd kompilatora C3771 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3771
dev_langs:
- C++
helpviewer_keywords:
- C3771
ms.assetid: 68c23b25-7f21-4eaa-8f7e-38fda1130a69
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2af9f58c533927b326ac39ff2f0c555d156dcaf3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079430"
---
# <a name="compiler-error-c3771"></a>Błąd kompilatora C3771

"identyfikator": deklaracja zaprzyjaźniona nie można znaleźć w najbliższym zakresie przestrzeni nazw

Deklaracja szablonu klasy dla określonego szablonu *identyfikator* nie można odnaleźć w bieżącym obszarze nazw.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Upewnij się, że deklaracja szablonu klasy dla identyfikatora szablonu jest zdefiniowana w bieżącej przestrzeni nazw lub identyfikator szablonu jest w pełni kwalifikowaną nazwę.

## <a name="example"></a>Przykład

Poniższy przykład kodu deklaruje szablonu klasy, a funkcja w przestrzeni nazw `NA`, ale próbuje zadeklarować zaprzyjaźnionego szablonu funkcji, w obszarze nazw `NB`.

```cpp
// C3771.cpp
// compile with: /c

namespace NA {
template<class T> class A {
    void aFunction(T t) {};
    };
}
// using namespace NA;
namespace NB {
    class X {
        template<class T> friend void A<T>::aFunction(T); // C3771
// try the following line instead
//      template<class T> friend void NA::A<T>::aFunction(T);
// or try "using namespace NA;" instead.
    };
}
```

## <a name="see-also"></a>Zobacz też

[Szablony](../../cpp/templates-cpp.md)