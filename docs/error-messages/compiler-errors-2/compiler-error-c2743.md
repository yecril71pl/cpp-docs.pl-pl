---
title: Błąd kompilatora C2743 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2743
dev_langs:
- C++
helpviewer_keywords:
- C2743
ms.assetid: 644cd444-21d2-471d-a176-f5f52c5a0b73
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4217a1e7a8475362c654ac34b6a345846341ec35
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056495"
---
# <a name="compiler-error-c2743"></a>Błąd kompilatora C2743

"type": nie można przechwycić natywnego typu destruktorem __clrcall lub konstruktorem kopiującym

Moduł skompilowany z **/CLR** podjęto próbę wykrycia tego typu natywnego i gdzie używa typu destruktorem lub konstruktorem kopiującym `__clrcall` konwencji wywoływania.

Gdy skompilowano z opcją **/CLR**, obsługa wyjątków oczekuje, że funkcje elementów członkowskich w typie natywnym za [__cdecl](../../cpp/cdecl.md) i nie [__clrcall](../../cpp/clrcall.md). Typy natywne za pomocą funkcji elementów członkowskich przy użyciu `__clrcall` konwencji wywoływania, nie można przechwycić w module, który został skompilowany przy użyciu **/CLR**.

Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2743.

```
// C2743.cpp
// compile with: /clr
public struct S {
   __clrcall ~S() {}
};

public struct T {
   ~T() {}
};

int main() {
   try {}
   catch(S) {}   // C2743
   // try the following line instead
   // catch(T) {}

   try {}
   catch(S*) {}   // OK
}
```