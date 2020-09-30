---
title: Błąd kompilatora C3171
ms.date: 11/04/2016
f1_keywords:
- C3171
helpviewer_keywords:
- C3171
ms.assetid: 1ce26997-7ef1-4c9f-84da-003ea1a4251e
ms.openlocfilehash: 14f0cedc5448005a29d74f05ae3e68e74eb5cf1c
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508300"
---
# <a name="compiler-error-c3171"></a>Błąd kompilatora C3171

"module": nie można określić innych atrybutów modułu w projekcie

atrybuty [modułu](../../windows/attributes/module-cpp.md) o różnych listach parametrów znaleziono w dwóch plikach w kompilacji. `module`Dla kompilacji można określić tylko jeden unikatowy atrybut.

Identyczne `module` atrybuty można określić w więcej niż jednym pliku kodu źródłowego.

Na przykład jeśli `module` znaleziono następujące atrybuty:

```cpp
// C3171.cpp
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.0") ];
int main() {}
```

A następnie

```cpp
// C3171b.cpp
// compile with: C3171.cpp
// C3171 expected
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.1") ];
```

kompilator generuje C3171 (zanotuj różne wartości wersji).
