---
title: Błąd kompilatora C3116
ms.date: 11/04/2016
f1_keywords:
- C3116
helpviewer_keywords:
- C3116
ms.assetid: 597463e1-a5cc-4ed3-a917-eae9a61d3312
ms.openlocfilehash: b336588d732fca2fd45b753429a563360f575912
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223450"
---
# <a name="compiler-error-c3116"></a>Błąd kompilatora C3116

"specyfikator magazynu": nieprawidłowa Klasa magazynu dla metody interfejsu

Użyto **`typedef`** , **`register`** , lub **`static`** jako klasy magazynu dla metody interfejsu. Te klasy magazynu są niedozwolone w składowych interfejsu.

Poniższy przykład generuje C3116:

```cpp
// C3116.cpp
__interface ImyInterface
{
   static void myFunc();   // C3116
};
```
