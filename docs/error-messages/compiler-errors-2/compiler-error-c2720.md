---
title: Błąd kompilatora C2720 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2720
dev_langs:
- C++
helpviewer_keywords:
- C2720
ms.assetid: 9ee3aab7-711b-4f5a-b2f1-cb62b130f1ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2d75c9847016102d4ae8609fb0a0a78726e4c67
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084019"
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