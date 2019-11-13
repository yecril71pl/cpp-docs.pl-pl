---
title: Ostrzeżenie kompilatora (poziom 1) C4600
ms.date: 11/04/2016
f1_keywords:
- C4600
helpviewer_keywords:
- C4600
ms.assetid: f023a2a1-7fc4-463f-a434-dc93fcd3f4e9
ms.openlocfilehash: 6eae37d006b5fcd6bd1c5e2993f1752c0534ee45
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966224"
---
# <a name="compiler-warning-level-1-c4600"></a>Ostrzeżenie kompilatora (poziom 1) C4600

\#pragma "Nazwa makra": oczekiwano prawidłowego ciągu niepustego

Nie można określić pustego ciągu podczas wypychania lub wyskakującej nazwy makra z [pop_macro](../../preprocessor/pop-macro.md) lub [push_macro](../../preprocessor/push-macro.md).

Poniższy przykład generuje C4600:

```cpp
// C4600.cpp
// compile with: /W1
int main()
{
   #pragma push_macro("")   // C4600 passing an empty string
}
```