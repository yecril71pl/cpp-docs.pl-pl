---
title: Kompilator ostrzeżenie (poziom 1) C4667 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4667
dev_langs:
- C++
helpviewer_keywords:
- C4667
ms.assetid: 5d2b7fe0-4f0e-4cd6-b432-ca02c3d194ab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2f6b341998caa519874e066bcc5e6a25651f0d47
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025467"
---
# <a name="compiler-warning-level-1-c4667"></a>Kompilator ostrzeżenie (poziom 1) C4667

'Funkcja': nie zdefiniowanego szablonu funkcji, który pasuje do wymuszonego wystąpienia

Nie można utworzyć wystąpienia szablonu funkcji, który nie został zadeklarowany.

Poniższy przykład spowoduje, że C4667:

```
// C4667a.cpp
// compile with: /LD /W1
template
void max(const int &, const int &); // C4667 expected
```

Aby uniknąć tego ostrzeżenia, najpierw należy zadeklarować szablonu funkcji:

```
// C4667b.cpp
// compile with: /LD
// Declare the function template
template<typename T>
const T &max(const T &a, const T &b) {
   return (a > b) ? a : b;
}
// Then forcibly instantiate it with a desired type ... i.e. 'int'
//
template
const int &max(const int &, const int &);
```