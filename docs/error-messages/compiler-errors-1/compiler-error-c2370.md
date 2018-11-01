---
title: Błąd kompilatora C2370
ms.date: 11/04/2016
f1_keywords:
- C2370
helpviewer_keywords:
- C2370
ms.assetid: 03403e8f-f393-47c4-bd25-5c1c7ea7d5cd
ms.openlocfilehash: 28c337a5cadfaeced39ee6ed73601338941029fc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471750"
---
# <a name="compiler-error-c2370"></a>Błąd kompilatora C2370

'Identyfikator': zmiana definicji; różne klasy magazynu

Identyfikator jest już zadeklarowana z klasą innego magazynu.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2370:

```
// C2370.cpp
// compile with: /Za /c
extern int i;
static int i;   // C2370
int i;   // OK
```

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2370:

```
// C2370b.cpp
#define Thread __declspec( thread )
extern int tls_i;
int Thread tls_i;   // C2370 declaration and the definition differ
int tls_i;   // OK
```