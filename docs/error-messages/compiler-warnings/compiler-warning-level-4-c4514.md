---
title: Kompilator ostrzeżenie (poziom 4) C4514
ms.date: 11/04/2016
f1_keywords:
- C4514
helpviewer_keywords:
- C4514
ms.assetid: cdae966a-9cd4-4e31-af30-2a014e68f614
ms.openlocfilehash: 0e8acdab20d5ba58b5bd8455fa538e5450518025
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658396"
---
# <a name="compiler-warning-level-4-c4514"></a>Kompilator ostrzeżenie (poziom 4) C4514

'Funkcja': Usunięto nieużywaną funkcję wbudowaną

Optymalizator usunięta funkcja śródwierszowa, który nie jest wywoływany.

To ostrzeżenie jest domyślnie wyłączona. Zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.

Poniższy przykład spowoduje wygenerowanie C4514:

```
// C4514.cpp
// compile with: /W4
#pragma warning(default : 4514)
class A
{
   public:
      void func()   // C4514, remove the function to resolve
      {
      }
};

int main()
{
}
```