---
title: Ostrzeżenie kompilatora (poziom 1) C4926
ms.date: 11/04/2016
f1_keywords:
- C4926
helpviewer_keywords:
- C4926
ms.assetid: 5717fce0-146f-4ef2-bde0-e9a01c0922d1
ms.openlocfilehash: 090b0b005c9374ad409ee580b3c726ce60db258f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174625"
---
# <a name="compiler-warning-level-1-c4926"></a>Ostrzeżenie kompilatora (poziom 1) C4926

"Identyfikator": symbol jest już zdefiniowany: atrybuty zostały zignorowane

Znaleziono deklarację do przodu, ale konstrukcja o tej samej nazwie już istnieje. Atrybuty deklaracji Forward są ignorowane.

Poniższy przykład generuje C4926:

```cpp
// C4926.cpp
// compile with: /W1
[module(name="MyLib")];

[coclass]
struct a {
};

[coclass]
struct a;   // C4926

int main() {
}
```
