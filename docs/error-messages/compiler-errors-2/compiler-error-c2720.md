---
title: Błąd kompilatora C2720
ms.date: 11/04/2016
f1_keywords:
- C2720
helpviewer_keywords:
- C2720
ms.assetid: 9ee3aab7-711b-4f5a-b2f1-cb62b130f1ce
ms.openlocfilehash: 24f4329ee631eafc7c2670d9ebf28609c22e7592
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202139"
---
# <a name="compiler-error-c2720"></a>Błąd kompilatora C2720

> "*Identyfikator*": specyfikator klasy magazynu "*specyfikator*" jest niedozwolony w składowych

Klasy Storage nie można używać w składowych klasy poza deklaracją. Aby naprawić ten błąd, Usuń niepotrzebny specyfikator [klasy magazynu](../../cpp/storage-classes-cpp.md) z definicji elementu członkowskiego spoza deklaracji klasy.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2720 i pokazuje, jak to naprawić:

```cpp
// C2720.cpp
struct S {
   static int i;
};
static S::i;   // C2720 - remove the unneeded 'static' to fix it
```
