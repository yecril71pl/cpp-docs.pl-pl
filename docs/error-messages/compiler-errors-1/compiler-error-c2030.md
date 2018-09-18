---
title: Błąd kompilatora C2030 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2030
dev_langs:
- C++
helpviewer_keywords:
- C2030
ms.assetid: 5806cead-64df-4eff-92de-52c9a3f5ee62
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b0c5849c372cc4c7ebf27dbe010e65d406ad1ab1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032905"
---
# <a name="compiler-error-c2030"></a>Błąd kompilatora C2030

destruktor z dostępnością "protected private" nie może być składową klasy zadeklarowanej jako "sealed"

Klasy Windows Runtime zadeklarowane jako `sealed` nie może mieć chronionego destruktora prywatnych. Publiczny wirtualny i prywatnych — wirtualne destruktory są dozwolone tylko w typach zapieczętowanych. Aby uzyskać więcej informacji, zobacz [klasy i struktury odwołania](../../cppcx/ref-classes-and-structs-c-cx.md).

Aby naprawić ten błąd, zmień dostępność elementu destruktor.