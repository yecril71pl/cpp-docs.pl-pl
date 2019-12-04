---
title: Błąd kompilatora C2825
ms.date: 11/04/2016
f1_keywords:
- C2825
helpviewer_keywords:
- C2825
ms.assetid: c832f1c1-5184-4fc2-9356-12b21daa7af3
ms.openlocfilehash: 6a51901477958056356a96d71adde4241d60a2ac
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750588"
---
# <a name="compiler-error-c2825"></a>Błąd kompilatora C2825

var: musi być klasą lub przestrzenią nazw, gdy następuje po niej znak "::"

Podjęto nieudaną próbę utworzenia nazwy kwalifikowanej.

Na przykład upewnij się, że kod nie zawiera deklaracji funkcji, której nazwa funkcji rozpoczyna się od::.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2825:

```cpp
// C2825.cpp
typedef int i;
int main() {
   int* p = new int;
   p->i::i();   // C2825
   // try the following line instead
   // p->i::~i();
}
```
