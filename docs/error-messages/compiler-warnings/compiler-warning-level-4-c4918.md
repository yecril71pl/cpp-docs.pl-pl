---
title: Ostrzeżenie kompilatora (poziom 4) C4918
ms.date: 11/04/2016
f1_keywords:
- C4918
helpviewer_keywords:
- C4918
ms.assetid: 1bcf6d35-3467-4aa8-b2ef-cb33f4e70238
ms.openlocfilehash: 801c22a45037492dc609d93c6339ab8feff30494
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988803"
---
# <a name="compiler-warning-level-4-c4918"></a>Ostrzeżenie kompilatora (poziom 4) C4918

"Character": nieprawidłowy znak na liście optymalizacji pragma

Na liście optymalizacji instrukcji " [Optimize](../../preprocessor/optimize.md) pragma" znaleziono nieznany znak.

Na przykład następująca instrukcja generuje C4918:

```cpp
// C4918.cpp
// compile with: /W4
#pragma optimize("X", on) // C4918 expected
int main()
{
}
```
