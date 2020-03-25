---
title: Ostrzeżenie kompilatora (poziom 4) C4565
ms.date: 08/27/2018
f1_keywords:
- C4565
helpviewer_keywords:
- C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
ms.openlocfilehash: 5eccb3c29da612a39f7fcdf4ef25dedb898c8d43
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198331"
---
# <a name="compiler-warning-level-4-c4565"></a>Ostrzeżenie kompilatora (poziom 4) C4565

> "*Function*": zmiana definicji; Symbol został poprzednio zadeklarowany za pomocą __declspec (*modyfikator*)

## <a name="remarks"></a>Uwagi

Symbol został ponownie zdefiniowany lub ponownie zadeklarowany, a druga definicja lub Deklaracja, w przeciwieństwie do pierwszej definicji lub deklaracji, nie miała modyfikatora `__declspec` (*modyfikator*). To ostrzeżenie jest informacje. Aby usunąć to ostrzeżenie, Usuń jedną z definicji.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4565:

```cpp
// C4565.cpp
// compile with: /W4 /LD
__declspec(noalias) void f();
void f();   // C4565
```
