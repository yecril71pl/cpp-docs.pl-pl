---
title: Błąd kompilatora C2195
ms.date: 11/04/2016
f1_keywords:
- C2195
helpviewer_keywords:
- C2195
ms.assetid: 9f9f035c-9c51-4173-a8ea-c6f907fc5c63
ms.openlocfilehash: 9d0fdb3623a86adb07e910b186305f3e468d24b8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50606456"
---
# <a name="compiler-error-c2195"></a>Błąd kompilatora C2195

'Identyfikator': jest segmentem danych

`code_seg` Pragma korzysta z nazwą segmentu, w ramach `data_seg` pragmy.

Poniższy przykład spowoduje wygenerowanie C2195:

```
// C2195.cpp
#pragma data_seg("MYDATA")
#pragma code_seg("MYDATA")   // C2195
#pragma code_seg("MYDATA2")   // OK
```