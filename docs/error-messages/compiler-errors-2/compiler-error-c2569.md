---
title: Błąd kompilatora C2569 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2569
dev_langs:
- C++
helpviewer_keywords:
- C2569
ms.assetid: 092bed1e-f631-436c-9586-7750629f6fac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9309576439a772427c6adcb6f94826a8f9230058
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078858"
---
# <a name="compiler-error-c2569"></a>Błąd kompilatora C2569

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