---
title: Błąd kompilatora C2720
ms.date: 11/04/2016
f1_keywords:
- C2720
helpviewer_keywords:
- C2720
ms.assetid: 9ee3aab7-711b-4f5a-b2f1-cb62b130f1ce
ms.openlocfilehash: c6499fd3f279099ea7c5b31860e70bdaa285e3f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383051"
---
# <a name="compiler-error-c2720"></a>Błąd kompilatora C2720

> "*identyfikator*": "*specyfikator*" Specyfikator klasy składującej niedozwolony dla składowych

Klasa magazynu nie można używać dla składowych klasy poza deklaracją. Aby naprawić ten błąd, należy usunąć niepotrzebne [klasę magazynu](../../cpp/storage-classes-cpp.md) specyfikator w definicji elementu członkowskiego poza deklaracją klasy.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2720 i pokazuje, jak go naprawić:

```cpp
// C2720.cpp
struct S {
   static int i;
};
static S::i;   // C2720 - remove the unneeded 'static' to fix it
```