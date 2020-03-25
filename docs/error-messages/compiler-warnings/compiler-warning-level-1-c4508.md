---
title: Ostrzeżenie kompilatora (poziom 1) C4508
ms.date: 11/04/2016
f1_keywords:
- C4508
helpviewer_keywords:
- C4508
ms.assetid: c05f113b-b789-4df0-a4ef-78bce4767021
ms.openlocfilehash: 54baf35eaeb5ef2c8add024f25c059480d60617b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186572"
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
