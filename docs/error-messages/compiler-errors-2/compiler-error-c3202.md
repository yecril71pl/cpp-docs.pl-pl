---
title: Błąd kompilatora C3202
ms.date: 11/04/2016
f1_keywords:
- C3202
helpviewer_keywords:
- C3202
ms.assetid: 23528a0c-5493-4804-9789-cd3c38e49fb9
ms.openlocfilehash: 5a81da1ee67d897b7a38d9968f7715be7b5af3d9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484932"
---
# <a name="compiler-error-c3202"></a>Błąd kompilatora C3202

"arg name": nieprawidłowy domyślny argument dla parametru szablonu "parametru", oczekiwano szablonu klasy

Został przekazany nieprawidłowy domyślny argument dla parametru szablonu.

Poniższy przykład spowoduje wygenerowanie C3202:

```
// C3202.cpp
template<typename T>
class X
{
};

class Z
{
};

template<template<typename U> class T1 = Z, typename T2> // C3202
class Y
{
};
```