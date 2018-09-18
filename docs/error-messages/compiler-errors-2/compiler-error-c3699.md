---
title: Błąd kompilatora C3699 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3699
dev_langs:
- C++
helpviewer_keywords:
- C3699
ms.assetid: 47c29afc-ab8b-4238-adfe-788dd6e00b3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 64e5a5bb98f9e8a6950bbb279c026f167a2ee92e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46107718"
---
# <a name="compiler-error-c3699"></a>Błąd kompilatora C3699

'operator': nie można użyć tego operatora pośredniego na typie "type"

Próbowano użyć operatora pośredniego, który nie jest dozwolona na `type`.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3699.

```
// C3699.cpp
// compile with: /clr /c
using namespace System;
int main() {
   String * s;   // C3699
   // try the following line instead
   // String ^ s2;
}
```

## <a name="example"></a>Przykład

Właściwość prosta nie może mieć typu referencyjnego. Zobacz [właściwość](../../windows/property-cpp-component-extensions.md) Aby uzyskać więcej informacji. Poniższy przykład spowoduje wygenerowanie C3699.

```
// C3699_b.cpp
// compile with: /clr /c
ref struct C {
   property System::String % x;   // C3699
   property System::String ^ y;   // OK
};
```

## <a name="example"></a>Przykład

Wielokrotność składni "wskaźnika do wskaźnika" jest uchwytem do odwołania śledzenia. Poniższy przykład spowoduje wygenerowanie C3699.

```
// C3699_c.cpp
// compile with: /clr /c
using namespace System;
void Test(String ^^ i);   // C3699
void Test2(String ^% i);
```