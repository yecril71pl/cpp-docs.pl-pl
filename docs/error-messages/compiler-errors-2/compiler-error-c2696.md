---
title: Błąd kompilatora C2696 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2696
dev_langs:
- C++
helpviewer_keywords:
- C2696
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e6e76b0c11d329c734b0609c540aca4315c7ed9f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108745"
---
# <a name="compiler-error-c2696"></a>Błąd kompilatora C2696

Nie można utworzyć tymczasowego obiektu tego typu zarządzanego "type"

Odwołuje się do `const` niezarządzanego w programie, że kompilator wywołanie konstruktora i utworzyć tymczasowego obiektu na stosie. Jednak klasy zarządzanej nigdy nie mogą być tworzone na stosie.

C2696 jest dostępna, przy użyciu opcji kompilatora przestarzałe **: oldsyntax**.
