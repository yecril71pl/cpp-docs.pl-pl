---
title: Kompilator ostrzeżenie (poziom 2) C4156 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4156
dev_langs:
- C++
helpviewer_keywords:
- C4156
ms.assetid: 9adf3acb-c0fe-42a8-a4db-5822b1493f77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eddce0944152fe95aa4ef2fd98ec30a793a90978
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084500"
---
# <a name="compiler-warning-level-2-c4156"></a>Kompilator ostrzeżenie (poziom 2) C4156

Usunięcie wyrażenia tablicowego bez użycia formularza tablicy "delete"; zastąpiono formularz tablicy

Inny niż tablica formie **Usuń** nie można usunąć tablicy. Kompilator przetłumaczył **Usuń** do formularza tablicy.

Ostrzeżenie to pojawia się tylko w ramach rozszerzenia Microsoft (/Ze).

## <a name="example"></a>Przykład

```
// C4156.cpp
// compile with: /W2
int main()
{
   int (*array)[ 10 ] = new int[ 5 ][ 10 ];
   delete array; // C4156, changed by compiler to "delete [] array;"
}
```