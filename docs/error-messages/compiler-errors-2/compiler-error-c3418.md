---
title: Błąd kompilatora C3418 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3418
dev_langs:
- C++
helpviewer_keywords:
- C3418
ms.assetid: 54042c04-3c45-41c1-bad7-90f9ee05a21b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 26fa67da6f24e578319660c17cb48d7d715be408
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033280"
---
# <a name="compiler-error-c3418"></a>Błąd kompilatora C3418

Specyfikator dostępu "specyfikatora" nie jest obsługiwana.

Specyfikator dostępu CLR została określona niepoprawnie.  Aby uzyskać więcej informacji, zobacz widoczność typów i element członkowski wglądu w [porady: definiowanie i Consume Classes and Structs (C + +/ interfejsu wiersza polecenia)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md).

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