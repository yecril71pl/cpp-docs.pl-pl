---
title: Błąd kompilatora C2346
ms.date: 11/04/2016
f1_keywords:
- C2346
helpviewer_keywords:
- C2346
ms.assetid: 246145be-5645-4cd6-867c-e3bc39e33dca
ms.openlocfilehash: a6d75ca671e22203cb40ca18de21606834eeefa8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188094"
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