---
title: Błąd kompilatora C3208 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3208
dev_langs:
- C++
helpviewer_keywords:
- C3208
ms.assetid: 6d060bfe-52cf-4599-8f70-bdeb5a670df3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 53564517eaed44c21e6eccb58ad6399788129687
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078507"
---
# <a name="compiler-error-c3208"></a>Błąd kompilatora C3208

'Funkcja': lista parametrów szablonu dla szablonu klasy "class" jest niezgodny z listy parametrów szablonu dla szablonu parametru szablonu "parametru"

Parametru szablonu nie ma taką samą liczbę parametrów szablonu jako szablon podanej klasy.

Poniższy przykład spowoduje wygenerowanie C3208:

```
// C3208.cpp
template <template <class T> class TT >
int f();

template <class T1, class T2>
struct S;

template <class T1>
struct R;

int i = f<S>();   // C3208
// try the following line instead
// int i = f<R>();
```