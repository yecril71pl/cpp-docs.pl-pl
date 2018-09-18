---
title: Błąd kompilatora C2346 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2346
dev_langs:
- C++
helpviewer_keywords:
- C2346
ms.assetid: 246145be-5645-4cd6-867c-e3bc39e33dca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ec916bcdce1a43c597d8cfae10e5393cbeb99ee
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108617"
---
# <a name="compiler-error-c2346"></a>Błąd kompilatora C2346

'Funkcja' nie może zostać skompilowana jako natywna: Przyczyna

Kompilator nie może skompilować funkcji na język MSIL.

Aby uzyskać więcej informacji, zobacz [zarządzane, niezarządzane](../../preprocessor/managed-unmanaged.md) i [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md).

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Usuń kod w funkcji, która nie można skompilować do MSIL.

1. Albo nie można skompilować moduł za pomocą **/CLR**, lub oznaczyć funkcji jako Niezarządzani z niezarządzanego pragmy.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2346.

```
// C2346.cpp
// processor: x86
// compile with: /clr
// C2346 expected
struct S
{
   S()
   {
      { __asm { nop } }
   }
   virtual __clrcall ~S() { }
};

void main()
{
   S s;
}
```