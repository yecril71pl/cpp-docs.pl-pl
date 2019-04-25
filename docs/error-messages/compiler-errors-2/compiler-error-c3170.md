---
title: Błąd kompilatora C3170
ms.date: 11/04/2016
f1_keywords:
- C3170
helpviewer_keywords:
- C3170
ms.assetid: ca9a59d6-7df3-42f0-b028-c09d0af3ac2a
ms.openlocfilehash: 5ef39e4580601dd90b5695d9115902bb5b834409
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174708"
---
# <a name="compiler-error-c3170"></a>Błąd kompilatora C3170

nie może posiadać innych identyfikatorów modułu w projekcie

[Moduł](../../windows/module-cpp.md) atrybuty pod różnymi nazwami zostały znalezione w dwóch plików w kompilacji. Tylko jeden unikatowy `module` atrybut może być określona dla kompilacji.

Identyczne `module` atrybuty można określić w więcej niż jeden plik kodu źródłowego.

Na przykład, jeśli znaleziono następujące atrybuty modułu:

```
// C3170.cpp
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];
int main() {}
```

Następnie wyszukaj maszynę

```
// C3170b.cpp
// compile with: C3170.cpp
// C3170 expected
[ module(name="MyModule1", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];
```

kompilator wygeneruje C3170 (Uwaga różne nazwy).