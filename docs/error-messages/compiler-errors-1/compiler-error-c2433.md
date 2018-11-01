---
title: Błąd kompilatora C2433
ms.date: 11/04/2016
f1_keywords:
- C2433
helpviewer_keywords:
- C2433
ms.assetid: 7079fedd-6059-4125-82ef-ebe275f1f9d1
ms.openlocfilehash: 8a98fcf7570605694569b7ae466ae0a3c7cf14bb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512061"
---
# <a name="compiler-error-c2433"></a>Błąd kompilatora C2433

'Identyfikator': 'modyfikator"nie jest dozwolone w deklaracjach danych

`friend`, `virtual`, I `inline` modyfikatorów nie można używać dla deklaracji danych.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2433.

```
// C2433.cpp
class C{};

int main() {
   inline C c;   // C2433
}
```