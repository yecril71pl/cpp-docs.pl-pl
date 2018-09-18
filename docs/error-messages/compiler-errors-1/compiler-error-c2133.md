---
title: Błąd kompilatora C2133 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2133
dev_langs:
- C++
helpviewer_keywords:
- C2133
ms.assetid: 8942f9e8-9818-468f-97db-09dbd124fcae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 169b24787f1b180c7ba70c5d779e341e60ea2150
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025194"
---
# <a name="compiler-error-c2133"></a>Błąd kompilatora C2133

'Identyfikator': nieznany rozmiar

Tablica bez określonego rozmiaru jest zadeklarowany jako członek klasy, struktury, Unii lub wyliczenia. Opcja/za (ANSI C) nie zezwala na tablice bez określonego rozmiaru elementu członkowskiego.

Poniższy przykład spowoduje wygenerowanie C2133:

```
// C2133.cpp
// compile with: /Za
struct X {
   int a[0];   // C2133 unsized array
};
```

Możliwe rozwiązanie:

```
// C2133b.cpp
// compile with: /c
struct X {
   int a[0];   // no /Za
};
```