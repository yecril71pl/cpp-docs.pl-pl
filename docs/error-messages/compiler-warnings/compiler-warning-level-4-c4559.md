---
title: Ostrzeżenie kompilatora (poziom 4) C4559
ms.date: 08/27/2018
f1_keywords:
- C4559
helpviewer_keywords:
- C4559
ms.assetid: ed542f60-454d-45cb-85da-987ede61b1ab
ms.openlocfilehash: 0788824dd4180476d81d9682f99fb95883b8c4f0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198344"
---
# <a name="compiler-warning-level-4-c4559"></a>Ostrzeżenie kompilatora (poziom 4) C4559

> "*Function*": zmiana definicji; Funkcja zyskuje __declspec (*modyfikator*)

## <a name="remarks"></a>Uwagi

Funkcja została ponownie zdefiniowana lub ponownie zadeklarowana, a druga definicja lub Deklaracja dodała modyfikator **__declspec** (*modyfikator*). To ostrzeżenie jest informacje. Aby usunąć to ostrzeżenie, Usuń jedną z definicji.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4559:

```cpp
// C4559.cpp
// compile with: /W4 /LD
void f();
__declspec(noalias) void f();   // C4559
```
