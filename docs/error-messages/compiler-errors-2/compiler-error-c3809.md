---
title: Błąd kompilatora C3809
ms.date: 11/04/2016
f1_keywords:
- C3809
helpviewer_keywords:
- C3809
ms.assetid: 37eca584-c20c-464e-8e45-a987214b7ce4
ms.openlocfilehash: 889d9a108ab0dfb0101fb9ec9c367db9378b1128
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757140"
---
# <a name="compiler-error-c3809"></a>Błąd kompilatora C3809

"Class": typ zarządzany lub WinRT nie może mieć żadnych zaprzyjaźnionych funkcji/klas/interfejsów

Typy zarządzane i typy środowisko wykonawcze systemu Windows nie pozwalają na korzystanie z znajomych. Aby naprawić ten błąd, nie deklaruj znajomych w typach zarządzanych lub środowisko wykonawcze systemu Windows.

Poniższy przykład generuje C3809:

```cpp
// C3809a.cpp
// compile with: /clr
ref class A {};

ref class B
{
public:
   friend ref class A;   // C3809
};

int main()
{
}
```
