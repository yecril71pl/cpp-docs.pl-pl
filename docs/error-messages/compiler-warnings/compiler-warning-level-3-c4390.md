---
title: Ostrzeżenie kompilatora (poziom 3) C4390
ms.date: 11/04/2016
f1_keywords:
- C4390
helpviewer_keywords:
- C4390
ms.assetid: c95c2f1b-9bce-4b1f-a80c-565d4cde0b1e
ms.openlocfilehash: 63150f4ca801d3c377c7bc09b58a778bebf02b46
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198682"
---
# <a name="compiler-warning-level-3-c4390"></a>Ostrzeżenie kompilatora (poziom 3) C4390

";": znaleziono pustą instrukcję sterowaną; Czy to jest zamiar?

Znaleziono średnik po instrukcji sterującej, która nie zawiera żadnych instrukcji.

W przypadku uzyskania C4390 z powodu makra należy użyć dyrektywy pragma [ostrzeżenia](../../preprocessor/warning.md) , aby wyłączyć C4390 w module zawierającym makro.

Poniższy przykład generuje C4390:

```cpp
// C4390.cpp
// compile with: /W3
int main() {
   int i = 0;
   if (i);   // C4390
      i++;
}
```
