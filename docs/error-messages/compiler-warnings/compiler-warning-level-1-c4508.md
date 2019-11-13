---
title: Ostrzeżenie kompilatora (poziom 1) C4508
ms.date: 11/04/2016
f1_keywords:
- C4508
helpviewer_keywords:
- C4508
ms.assetid: c05f113b-b789-4df0-a4ef-78bce4767021
ms.openlocfilehash: 394a59a472100cc30476b5bb87f30c45d867f94b
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966306"
---
# <a name="compiler-warning-level-1-c4508"></a>Ostrzeżenie kompilatora (poziom 1) C4508

"Function": funkcja powinna zwrócić wartość; Założono typ zwracany "void"

Nie określono zwracanego typu funkcji. W takim przypadku C4430 powinna również być wyzwalana, a kompilator implementuje poprawkę zgłoszoną przez C4430 (wartość domyślna to int).

Aby usunąć to ostrzeżenie, jawnie Zadeklaruj zwracany typ funkcji.

Poniższy przykład generuje C4508:

```cpp
// C4508.cpp
// compile with: /W1 /c
#pragma warning (disable : 4430)
func() {}   // C4508
void func2() {}   // OK
```