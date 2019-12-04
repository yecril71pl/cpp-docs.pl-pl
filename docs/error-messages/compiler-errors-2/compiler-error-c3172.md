---
title: Błąd kompilatora C3172
ms.date: 11/04/2016
f1_keywords:
- C3172
helpviewer_keywords:
- C3172
ms.assetid: 1834e2fd-6036-4c33-aff2-b51bc7c99441
ms.openlocfilehash: 1da2676d660d23e3fb71b56263779b1f1edacbf9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761741"
---
# <a name="compiler-error-c3172"></a>Błąd kompilatora C3172

"module_name": nie można określić różnych atrybutów idl_module w projekcie

[idl_module](../../windows/idl-module.md) atrybuty o tej samej nazwie, ale w dwóch plikach w kompilacji znaleziono różne parametry `dllname` lub `version`. Dla kompilacji można określić tylko jeden unikatowy atrybut `idl_module`.

Identyczne atrybuty `idl_module` można określić w więcej niż jednym pliku kodu źródłowego.

Na przykład jeśli znaleziono następujące atrybuty `idl_module`:

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
