---
title: Błąd kompilatora C2289
ms.date: 11/04/2016
f1_keywords:
- C2289
helpviewer_keywords:
- C2289
ms.assetid: cb41a29e-1b06-47dc-bfce-8d73bd63a0df
ms.openlocfilehash: 239552eb383197e57fcc6285cbf416c7c71c858b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216274"
---
# <a name="compiler-error-c2289"></a>Błąd kompilatora C2289

kwalifikator tego samego typu użyty więcej niż raz

Deklaracja typu lub definicja używa kwalifikatora typu ( **`const`** , **`volatile`** , **`signed`** lub **`unsigned`** ) więcej niż raz, co powoduje błąd pod kątem zgodności ze standardem ANSI (**/za**).

Poniższy przykład generuje C2286:

```cpp
// C2289.cpp
// compile with: /Za /c
volatile volatile int i;   // C2289
volatile int j;   // OK
```
