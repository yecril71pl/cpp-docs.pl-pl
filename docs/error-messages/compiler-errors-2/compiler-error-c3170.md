---
title: Błąd kompilatora C3170
ms.date: 11/04/2016
f1_keywords:
- C3170
helpviewer_keywords:
- C3170
ms.assetid: ca9a59d6-7df3-42f0-b028-c09d0af3ac2a
ms.openlocfilehash: e2d74a637e2902fcf636b49068882f32aa706f94
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761767"
---
# <a name="compiler-error-c3170"></a>Błąd kompilatora C3170

nie może mieć innych identyfikatorów modułu w projekcie

atrybuty [modułu](../../windows/module-cpp.md) o różnych nazwach znajdują się w dwóch plikach w kompilacji. Dla kompilacji można określić tylko jeden unikatowy atrybut `module`.

Identyczne atrybuty `module` można określić w więcej niż jednym pliku kodu źródłowego.

Na przykład jeśli znaleziono następujące atrybuty modułu:

```cpp
// C3170.cpp
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];
int main() {}
```

A następnie

```cpp
// C3170b.cpp
// compile with: C3170.cpp
// C3170 expected
[ module(name="MyModule1", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];
```

kompilator generuje C3170 (należy pamiętać o różnych nazwach).
