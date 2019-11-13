---
title: Ostrzeżenie kompilatora (poziom 1) C4348
ms.date: 11/04/2016
f1_keywords:
- C4348
helpviewer_keywords:
- C4348
ms.assetid: 816010eb-6079-48d5-a41b-0fc4d67cfe4c
ms.openlocfilehash: 022b71a27819934d444f5ffd9811b62cf1012abb
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73964955"
---
# <a name="compiler-warning-level-1-c4348"></a>Ostrzeżenie kompilatora (poziom 1) C4348

"Type": Ponowna definicja domyślnego parametru: numer parametru

Parametr szablonu został ponownie zdefiniowany.

Poniższy przykład generuje C4348:

```cpp
// C4348.cpp
// compile with: /LD /W1
template <class T=int> struct A;   // forward declaration

template <class T=int> struct A { };
// C4348, redefinition of default parameter
// try the following line instead
// template <class T> struct A { };
```