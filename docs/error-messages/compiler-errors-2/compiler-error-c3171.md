---
title: Błąd kompilatora C3171
ms.date: 11/04/2016
f1_keywords:
- C3171
helpviewer_keywords:
- C3171
ms.assetid: 1ce26997-7ef1-4c9f-84da-003ea1a4251e
ms.openlocfilehash: 602c9ca1051646fca2c5788c036354047fad2522
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599484"
---
# <a name="compiler-error-c3171"></a>Błąd kompilatora C3171

"module": nie można określić innych atrybutów modułu w projekcie

[Moduł](../../windows/module-cpp.md) znaleziono atrybuty z listy różnych parametrów w dwóch plików w kompilacji. Tylko jeden unikatowy `module` atrybut może być określona dla kompilacji.

Identyczne `module` atrybuty można określić w więcej niż jeden plik kodu źródłowego.

Na przykład jeśli następujące `module` znaleziono atrybuty:

```
// C3171.cpp
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.0") ];
int main() {}
```

Następnie wyszukaj maszynę

```
// C3171b.cpp
// compile with: C3171.cpp
// C3171 expected
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.1") ];
```

kompilator wygeneruje C3171 (Zwróć uwagę na wartości różnych wersji).