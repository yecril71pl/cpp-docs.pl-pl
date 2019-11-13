---
title: Ostrzeżenie kompilatora (poziom 1) C4548
ms.date: 11/04/2016
f1_keywords:
- C4548
helpviewer_keywords:
- C4548
ms.assetid: 2cee817e-e463-4d90-bbd2-de120d48c101
ms.openlocfilehash: 09d2d2d1b67b203ebbc6b62b5b19f4b063e312c3
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966408"
---
# <a name="compiler-warning-level-1-c4548"></a>Ostrzeżenie kompilatora (poziom 1) C4548

wyrażenie przed przecinkiem nie przynosi efektu; oczekiwane wyrażenie, który przynosi efekt

Kompilator wykrył nieprawidłowo sformułowane wyrażenie przecinka.

To ostrzeżenie jest domyślnie wyłączone. Aby uzyskać więcej informacji, zobacz [ostrzeżenia kompilatora, które są domyślnie wyłączone](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

Poniższy przykład generuje C4548:

```cpp
// C4548.cpp
// compile with: /W1
#pragma warning (default : 4548)
int main()
{
   int i = 0, k = 0;

   if ( i, k )   // C4548
   // try the following line instead
   // if ( i = 0, k )
      i++;
}
```