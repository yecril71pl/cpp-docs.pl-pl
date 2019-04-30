---
title: Kompilator ostrzeżenie (poziom 1) C4052
ms.date: 11/04/2016
f1_keywords:
- C4052
helpviewer_keywords:
- C4052
ms.assetid: f9955421-16ab-46e5-8f9d-bf1639a519ef
ms.openlocfilehash: c7d2a603b7ec97889b075c7a67e5b8439ad487af
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388647"
---
# <a name="compiler-warning-level-1-c4052"></a>Kompilator ostrzeżenie (poziom 1) C4052

deklaracje funkcji, inny, jeden z nich zawiera zmienne argumenty

Jedna deklaracja funkcji nie zawiera zmiennych argumentów. Jest on ignorowany.

Poniższy przykład spowoduje wygenerowanie C4052:

```
// C4052.c
// compile with: /W4 /c
int f();
int f(int i, ...);   // C4052
```