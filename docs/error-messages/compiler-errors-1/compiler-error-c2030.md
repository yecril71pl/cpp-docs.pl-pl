---
title: Błąd kompilatora C2030
ms.date: 11/04/2016
f1_keywords:
- C2030
helpviewer_keywords:
- C2030
ms.assetid: 5806cead-64df-4eff-92de-52c9a3f5ee62
ms.openlocfilehash: 217f97d205e1da075277b8b0bc22ff3baab13482
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602179"
---
# <a name="compiler-error-c2030"></a>Błąd kompilatora C2030

destruktor z dostępnością "protected private" nie może być składową klasy zadeklarowanej jako "sealed"

Klasy Windows Runtime zadeklarowane jako `sealed` nie może mieć chronionego destruktora prywatnych. Publiczny wirtualny i prywatnych — wirtualne destruktory są dozwolone tylko w typach zapieczętowanych. Aby uzyskać więcej informacji, zobacz [klasy i struktury odwołania](../../cppcx/ref-classes-and-structs-c-cx.md).

Aby naprawić ten błąd, zmień dostępność elementu destruktor.