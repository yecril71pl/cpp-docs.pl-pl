---
title: Błąd kompilatora C3387
ms.date: 11/04/2016
f1_keywords:
- C3387
helpviewer_keywords:
- C3387
ms.assetid: c54d9925-ed14-4976-b8db-e8d4dc84e536
ms.openlocfilehash: 9f083f5c21e494d08374e72155b44ee14719881f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743149"
---
# <a name="compiler-error-c3387"></a>Błąd kompilatora C3387

nie można zastosować elementu "member": __declspec (dllexport)/\__declspec (dllimport) do składowej typu zarządzanego lub WinRT

Modyfikatory `__declspec` `dllimport` i [dllexport](../../cpp/dllexport-dllimport.md) nie są prawidłowe dla elementów członkowskich typu zarządzanego lub środowisko wykonawcze systemu Windows.

Poniższy przykład generuje C3387 i pokazuje, jak to naprawić:

```cpp
// C3387a.cpp
// compile with: /clr /c
ref class X2 {
   void __declspec(dllexport) mf() {   // C3387
   // try the following line instead
   // void mf() {
   }
};
```
