---
title: Ostrzeżenie kompilatora (poziom 1) C4076
ms.date: 11/04/2016
f1_keywords:
- C4076
helpviewer_keywords:
- C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
ms.openlocfilehash: 1958aec4d6642188af1467ab4cab1ecf55c29165
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223320"
---
# <a name="compiler-warning-level-1-c4076"></a>Ostrzeżenie kompilatora (poziom 1) C4076

> *modyfikator "Type*": nie może być używany z typem "*TypeName*"

## <a name="remarks"></a>Uwagi

Modyfikator typu, niezależnie od tego, czy jest **`signed`** lub **`unsigned`** , nie może być używany z typem innym niż Integer. *modyfikator typu* jest ignorowany.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4076; Aby rozwiązać ten problem, Usuń **`unsigned`** modyfikator typu:

```cpp
// C4076.cpp
// compile with: /W1 /LD
unsigned double x;   // C4076
```
