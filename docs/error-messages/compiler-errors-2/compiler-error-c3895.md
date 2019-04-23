---
title: Błąd kompilatora C3895
ms.date: 11/04/2016
f1_keywords:
- C3895
helpviewer_keywords:
- C3895
ms.assetid: 771b9fe5-d6d4-4297-bf57-e2f857722155
ms.openlocfilehash: c4b1cad9ef48f1f16b411aab46e1bb9285d69ff3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779301"
---
# <a name="compiler-error-c3895"></a>Błąd kompilatora C3895

"var": elementy członkowskie typu danych nie może być "volatile"

Niektóre rodzaje składowych danych, na przykład [literału](../../extensions/literal-cpp-component-extensions.md) lub [initonly](../../dotnet/initonly-cpp-cli.md), nie może być [volatile](../../cpp/volatile-cpp.md).

Poniższy przykład spowoduje wygenerowanie C3895:

```
// C3895.cpp
// compile with: /clr
ref struct Y1 {
   initonly
   volatile int data_var2;   // C3895
};
```