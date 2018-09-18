---
title: Błąd kompilatora C3171 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3171
dev_langs:
- C++
helpviewer_keywords:
- C3171
ms.assetid: 1ce26997-7ef1-4c9f-84da-003ea1a4251e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 32c58f2ecd9651c347f45c29139ffe0ed65a6e3b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082264"
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