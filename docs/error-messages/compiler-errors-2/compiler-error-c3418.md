---
title: Błąd kompilatora C3418
ms.date: 11/04/2016
f1_keywords:
- C3418
helpviewer_keywords:
- C3418
ms.assetid: 54042c04-3c45-41c1-bad7-90f9ee05a21b
ms.openlocfilehash: 21023bfb551a1894e25cc4940892dde0f0440a0e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200890"
---
# <a name="compiler-error-c3418"></a>Błąd kompilatora C3418

specyfikator dostępu "specyfikator" nie jest obsługiwany

Określono nieprawidłowy specyfikator dostępu CLR.  Aby uzyskać więcej informacji, zobacz widoczność typów i widoczność elementów członkowskich w [instrukcje: Definiowanie i korzystanie z klas i strukturC++(/CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C3418.

```cpp
// C3418.cpp
// compile with: /clr /c
ref struct m {
internal public:   // C3418
   void test(){}
};

ref struct n {
internal:   // OK
   void test(){}
};
```
