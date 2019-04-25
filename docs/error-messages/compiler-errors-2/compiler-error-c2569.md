---
title: Compiler Error C2569
ms.date: 11/04/2016
f1_keywords:
- C2569
helpviewer_keywords:
- C2569
ms.assetid: 092bed1e-f631-436c-9586-7750629f6fac
ms.openlocfilehash: 1344bd8bde532d2e813ca03e173b995e935c76b2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62243763"
---
# <a name="compiler-error-c2569"></a>Compiler Error C2569

"EnumOrUnion": wyliczenia/Unii nie można użyć jako klasa bazowa

Typ musi pochodzić od określonego Unii lub wyliczenia, zmiana związek lub wyliczenie do klasy lub struktury.

Poniższy przykład spowoduje wygenerowanie C2569:

```
// C2569.cpp
// compile with: /c
union ubase {};
class cHasPubUBase : public ubase {};   // C2569
// OK
struct sbase {};
class cHasPubUBase : public sbase {};
```