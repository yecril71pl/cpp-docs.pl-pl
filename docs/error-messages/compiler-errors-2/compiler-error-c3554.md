---
title: Błąd kompilatora C3554
ms.date: 11/04/2016
f1_keywords:
- C3554
helpviewer_keywords:
- C3554
ms.assetid: aede18d5-fefc-4da9-9b69-adfe90bfa742
ms.openlocfilehash: 8bc9c465d16aea4714916fa6aa2942eb81c19015
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344567"
---
# <a name="compiler-error-c3554"></a>Błąd kompilatora C3554

"decltype" nie można łączyć z jakimkolwiek innym specyfikatorem typu

Nie kwalifikujesz się do `decltype()` — słowo kluczowe ze specyfikatorem dowolnego typu. Na przykład poniższy fragment kodu powoduje błąd C3554.

```
int x;
unsigned decltype(x); // C3554
```