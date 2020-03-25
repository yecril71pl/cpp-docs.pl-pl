---
title: Ostrzeżenie kompilatora (poziom 1) C4076
ms.date: 11/04/2016
f1_keywords:
- C4076
helpviewer_keywords:
- C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
ms.openlocfilehash: 77efeae27a67ea844759fd9980801d3daf788e89
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200266"
---
# <a name="compiler-warning-level-1-c4076"></a>Ostrzeżenie kompilatora (poziom 1) C4076

> *modyfikator "Type*": nie może być używany z typem "*TypeName*"

## <a name="remarks"></a>Uwagi

Modyfikator typu, niezależnie od tego, czy jest **podpisany** lub **niepodpisany**, nie może być używany z typem innym niż Integer. *modyfikator typu* jest ignorowany.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4076; Aby rozwiązać ten problem, Usuń modyfikator typu **bez znaku** :

```cpp
// C4076.cpp
// compile with: /W1 /LD
unsigned double x;   // C4076
```
