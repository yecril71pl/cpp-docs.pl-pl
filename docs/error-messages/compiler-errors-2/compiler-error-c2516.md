---
title: Błąd kompilatora C2516
ms.date: 11/04/2016
f1_keywords:
- C2516
helpviewer_keywords:
- C2516
ms.assetid: cd3accc1-0179-4a13-9587-616908c4ad1d
ms.openlocfilehash: 678c90c5f4d41b0a05bbb07f2aada82e9bfcdb1e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214662"
---
# <a name="compiler-error-c2516"></a>Błąd kompilatora C2516

"name": nie jest dozwoloną klasą bazową

Klasa pochodzi od nazwy typu zdefiniowanej przez **`typedef`** instrukcję.

Poniższy przykład generuje C2516:

```cpp
// C2516.cpp
typedef unsigned long ulong;
class C : public ulong {}; // C2516
```
