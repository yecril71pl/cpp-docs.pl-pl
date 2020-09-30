---
title: Błąd kompilatora C3172
ms.date: 11/04/2016
f1_keywords:
- C3172
helpviewer_keywords:
- C3172
ms.assetid: 1834e2fd-6036-4c33-aff2-b51bc7c99441
ms.openlocfilehash: ca0eab35f6e60d81a324156905619ceb7ace8830
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508294"
---
# <a name="compiler-error-c3172"></a>Błąd kompilatora C3172

"module_name": nie można określić różnych atrybutów idl_module w projekcie

[idl_module](../../windows/attributes/idl-module.md) atrybuty o tej samej nazwie, ale różne `dllname` lub `version` Parametry znajdują się w dwóch plikach w kompilacji. `idl_module`Dla kompilacji można określić tylko jeden unikatowy atrybut.

Identyczne `idl_module` atrybuty można określić w więcej niż jednym pliku kodu źródłowego.

Na przykład jeśli `idl_module` znaleziono następujące atrybuty:

```cpp
// C3172.cpp
[module(name="MyMod")];
[ idl_module(name="x", dllname="file.dll", version="1.1") ];
int main() {}
```

A następnie

```cpp
// C3172b.cpp
// compile with: C3172.cpp
// C3172 expected
[ idl_module(name="x", dllname="file.dll", version="1.0") ];
```

kompilator generuje C3172 (zanotuj różne wartości wersji).
