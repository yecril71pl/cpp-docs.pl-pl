---
title: Kompilator ostrzeżenie (poziom 1) C4544 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4544
dev_langs:
- C++
helpviewer_keywords:
- C4544
ms.assetid: 11ee04df-41ae-435f-af44-881e801315a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c7cd274f0d1b595d374e1b108db40a51395b968
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084279"
---
# <a name="compiler-warning-level-1-c4544"></a>Kompilator ostrzeżenie (poziom 1) C4544

"deklaracją": domyślny argument szablonu został zignorowany dla tej deklaracji szablonu

Domyślny argument szablonu został określony w nieprawidłowej lokalizacji i został zignorowany. Domyślny argument szablonu dla szablonu klasy można określić tylko w deklaracji lub definicji szablonu klasy a nie w składowej szablonu klasy.

Ten przykład generuje C4545 i następny przykład pokazuje, jak go naprawić:

```
// C4544.cpp
// compile with: /W1 /LD
template <class T>
struct S
{
   template <class T1>
      struct S1;
   void f();
};

template <class T=int>
template <class T1>
struct S<T>::S1 {};   // C4544
```

W tym przykładzie parametr domyślny ma zastosowanie do szablonu klasy `S`:

```
// C4544b.cpp
// compile with: /LD
template <class T = int>
struct S
{
   template <class T1>
      struct S1;
   void f();
};

template <class T>
template <class T1>
struct S<T>::S1 {};
```