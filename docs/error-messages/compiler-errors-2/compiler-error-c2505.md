---
title: Błąd kompilatora C2505
ms.date: 11/04/2016
f1_keywords:
- C2505
helpviewer_keywords:
- C2505
ms.assetid: b19f5c53-399d-425e-90db-fe3ca9b40858
ms.openlocfilehash: 94a6f180c93839646d771509145b2f65a00780fd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746867"
---
# <a name="compiler-error-c2505"></a>Błąd kompilatora C2505

"symbol": "__declspec (modifer)" można stosować tylko do deklaracji lub definicji obiektów globalnych lub statycznych elementów członkowskich danych

Modyfikator `__declspec`, który jest przeznaczony do użycia tylko w zakresie globalnym, został użyty w funkcji.

Aby uzyskać więcej informacji, zobacz temat [AppDomain](../../cpp/appdomain.md) i [Process](../../cpp/process.md).

Poniższy przykład generuje C2505:

```cpp
// C2505.cpp
// compile with: /clr

// OK
__declspec(process) int ii;
__declspec(appdomain) int jj;

int main() {
   __declspec(process) int i;   // C2505
   __declspec(appdomain) int j;   // C2505
}
```
