---
title: Ostrzeżenie kompilatora (poziom 4) C4611
ms.date: 11/04/2016
f1_keywords:
- C4611
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
ms.openlocfilehash: 2ce261b36344126d541a9b453c88f7f8289ecba0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214337"
---
# <a name="compiler-warning-level-4-c4611"></a>Ostrzeżenie kompilatora (poziom 4) C4611

Interakcja między "funkcją" i zniszczeniem obiektu języka C++ nie jest przenośna

Na niektórych platformach funkcje, które obejmują, **`catch`** mogą nie obsługiwać semantyki obiektów w języku C++, gdy jest poza zakresem.

Aby uniknąć nieoczekiwanego zachowania, należy unikać używania **`catch`** w funkcjach, które mają konstruktory i destruktory.

To ostrzeżenie jest wysyłane tylko raz; Zobacz [pragma warning](../../preprocessor/warning.md).
