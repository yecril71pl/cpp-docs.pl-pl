---
title: Błąd kompilatora C2768 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2768
dev_langs:
- C++
helpviewer_keywords:
- C2768
ms.assetid: a7f6047a-6a80-4737-ad5c-c12868639fb5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c76173f99dbc2fb415b60212109242845501694
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109109"
---
# <a name="compiler-error-c2768"></a>Błąd kompilatora C2768

'Funkcja': niedozwolone użycie argumentów jawnego szablonu

Kompilator nie może określić, jeśli definicja funkcji została powinien być jawna specjalizacja szablonu funkcji lub definicji funkcji została powinna być dla nowych funkcji.

Ten błąd został wprowadzony w Visual Studio .NET 2003 w jako część ulepszenia zgodności kompilatora.

Poniższy przykład spowoduje wygenerowanie C2768:

```
// C2768.cpp
template<typename T>
void f(T) {}

void f<int>(int) {}   // C2768

// an explicit specialization
template<>
void f<int>(int) {}

// global nontemplate function overload
void f(int) {}
```