---
title: Błąd kompilatora C2505
ms.date: 11/04/2016
f1_keywords:
- C2505
helpviewer_keywords:
- C2505
ms.assetid: b19f5c53-399d-425e-90db-fe3ca9b40858
ms.openlocfilehash: eabed85c61eaaa43b0106e0011f0357ece2e1ae1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221175"
---
# <a name="compiler-error-c2505"></a>Błąd kompilatora C2505

"symbol": "__declspec (modifer)" można stosować tylko do deklaracji lub definicji obiektów globalnych lub statycznych elementów członkowskich danych

**`__declspec`** Modyfikator, który jest przeznaczony do użycia tylko w zakresie globalnym, został użyty w funkcji.

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
