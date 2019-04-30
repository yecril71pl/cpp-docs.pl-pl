---
title: Błąd kompilatora C3200
ms.date: 11/04/2016
f1_keywords:
- C3200
helpviewer_keywords:
- C3200
ms.assetid: 44bb5e77-f0ec-421c-a732-b9ee7c0a3529
ms.openlocfilehash: 7eb0c00f4f4c5c59766bf305acfef89e12a6cfb1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402778"
---
# <a name="compiler-error-c3200"></a>Błąd kompilatora C3200

"template": nieprawidłowy argument szablonu dla parametru szablonu "parametru", oczekiwano szablonu klasy

Nieprawidłowy argument jest przekazywany do szablonu klasy. Szablon klasy oczekuje, że szablon jako parametr. W poniższym przykładzie wywołanie `Y<int, int> aY` wygeneruje C3200. Pierwszy parametr musi być szablonem, takich jak `Y<X, int> aY`.

```
// C3200.cpp
template<typename T>
class X
{
};

template<template<typename U> class T1, typename T2>
class Y
{
};

int main()
{
   Y<int, int> y;   // C3200
}
```