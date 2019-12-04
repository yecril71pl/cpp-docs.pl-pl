---
title: Błąd kompilatora C3171
ms.date: 11/04/2016
f1_keywords:
- C3171
helpviewer_keywords:
- C3171
ms.assetid: 1ce26997-7ef1-4c9f-84da-003ea1a4251e
ms.openlocfilehash: a3af19fa6b4f4def9bb42325f648109cfafcdaef
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761754"
---
# <a name="compiler-error-c3171"></a>Błąd kompilatora C3171

"module": nie można określić innych atrybutów modułu w projekcie

atrybuty [modułu](../../windows/module-cpp.md) o różnych listach parametrów znaleziono w dwóch plikach w kompilacji. Dla kompilacji można określić tylko jeden unikatowy atrybut `module`.

Identyczne atrybuty `module` można określić w więcej niż jednym pliku kodu źródłowego.

Na przykład jeśli znaleziono następujące atrybuty `module`:

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
