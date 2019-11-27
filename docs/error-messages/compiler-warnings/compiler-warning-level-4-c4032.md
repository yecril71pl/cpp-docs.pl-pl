---
title: Ostrzeżenie kompilatora (poziom 4) C4032
ms.date: 11/04/2016
f1_keywords:
- C4032
helpviewer_keywords:
- C4032
ms.assetid: 70dd0c85-0239-43f9-bb06-507f6a57d206
ms.openlocfilehash: 52e80340a5157e9350b6d4bbf3bcabea0487e089
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541258"
---
# <a name="compiler-warning-level-4-c4032"></a>Ostrzeżenie kompilatora (poziom 4) C4032

formalny parametr "number" ma inny typ podczas podwyższania poziomu

Typ parametru jest niezgodny, za pomocą domyślnej promocji, z typem w poprzedniej deklaracji.

Jest to błąd w języku ANSI C ([/za](../../build/reference/za-ze-disable-language-extensions.md)) i ostrzeżenie w ramach rozszerzeń Microsoft (/ze).

## <a name="example"></a>Przykład

```c
// C4032.c
// compile with: /W4
void func();
void func(char);   // C4032, char promotes to int

int main()
{
}
```