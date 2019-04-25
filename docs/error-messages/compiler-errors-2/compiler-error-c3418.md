---
title: Błąd kompilatora C3418
ms.date: 11/04/2016
f1_keywords:
- C3418
helpviewer_keywords:
- C3418
ms.assetid: 54042c04-3c45-41c1-bad7-90f9ee05a21b
ms.openlocfilehash: 8456e9b17b72cd4ac98349d2f2871a1c59f56911
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62311499"
---
# <a name="compiler-error-c3418"></a>Błąd kompilatora C3418

Specyfikator dostępu "specyfikatora" nie jest obsługiwana.

Specyfikator dostępu CLR została określona niepoprawnie.  Aby uzyskać więcej informacji, zobacz widoczność typów i element członkowski wglądu w [jak: Definiowanie oraz stosowanie klas i struktur (C++sposób niezamierzony)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3418.

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