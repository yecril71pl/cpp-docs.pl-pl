---
title: Ostrzeżenie kompilatora (poziom 1) C4555
ms.date: 11/04/2016
f1_keywords:
- C4555
helpviewer_keywords:
- C4555
ms.assetid: 50b286c1-f7bf-4292-b1fa-baaac9538611
ms.openlocfilehash: fb3373178ebb53d7b14228a361fcc2f0a08c873b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162364"
---
# <a name="compiler-warning-level-1-c4555"></a>Ostrzeżenie kompilatora (poziom 1) C4555

wyrażenie nie przynosi efektu; oczekiwane wyrażenie, który przynosi efekt

To ostrzeżenie informuje, gdy wyrażenie nie ma wpływu.

To ostrzeżenie jest domyślnie wyłączone. Aby uzyskać więcej informacji [, zobacz ostrzeżenia kompilatora, które są domyślnie wyłączone](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

Na przykład:

```cpp
// C4555.cpp
// compile with: /W1
#pragma warning(default:4555)

void func1()
{
   1;   // C4555
}

void func2()
{
   int x;
   x;   // C4555
}

int main()
{
}
```
