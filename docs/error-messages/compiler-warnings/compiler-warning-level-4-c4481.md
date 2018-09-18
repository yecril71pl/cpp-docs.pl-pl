---
title: Kompilator ostrzeżenie (poziom 4) C4481 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4481
dev_langs:
- C++
helpviewer_keywords:
- C4481
ms.assetid: 7bfd4e0c-b452-4e6c-b7c4-ac5cc93fe4ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 48ed2ba08423f7540f4e0a855aacbcab993d41aa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063765"
---
# <a name="compiler-warning-level-4-c4481"></a>Kompilator ostrzeżenie (poziom 4) C4481

użyte rozszerzenie niestandardowe: specyfikator "— słowo kluczowe" override

Słowo kluczowe użyto nie znajduje się w C++, standardowa, na przykład jeden specyfikatorów przesłonięć, które działa także w ramach/CLR.  Aby uzyskać więcej informacji, zobacz,

- [/clr (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Specyfikatory przesłonięć](../../windows/override-specifiers-cpp-component-extensions.md)

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4481.

```
// C4481.cpp
// compile with: /W4 /c
class B {
   virtual void f(unsigned);
};

class C : B {
   void f(unsigned) override;   // C4481
   void f2(unsigned);
};
```