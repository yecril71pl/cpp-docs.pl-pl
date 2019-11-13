---
title: Ostrzeżenie kompilatora (poziom 1) C4441
ms.date: 11/04/2016
f1_keywords:
- C4441
helpviewer_keywords:
- C4441
ms.assetid: 7fc540a5-e41f-47cf-aa37-b2b699c2685e
ms.openlocfilehash: 6f45288e1e52d157e5c135a45c0801a909fccfbc
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966021"
---
# <a name="compiler-warning-level-1-c4441"></a>Ostrzeżenie kompilatora (poziom 1) C4441

Zignorowano konwencję wywoływania elementu "CC1"; Zamiast tego użyto "CC2"

Funkcje członkowskie w typach zarządzanych przez użytkownika i ogólnych funkcjach globalnych muszą używać konwencji wywoływania [__clrcall](../../cpp/clrcall.md) .  Kompilator używany `__clrcall`.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4441.

```cpp
// C4441.cpp
// compile with: /clr /W1 /c
generic <class ItemType>
void __cdecl Test(ItemType item) {}   // C4441
// try the following line instead
// void Test(ItemType item) {}

ref struct MyStruct {
   void __cdecl Test(){}   // C4441
   void Test2(){}   // OK
};
```