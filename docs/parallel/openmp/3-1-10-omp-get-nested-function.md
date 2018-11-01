---
title: 3.1.10 Funkcja omp_get_nested
ms.date: 11/04/2016
ms.assetid: 48736a25-5c6e-4e2d-aad0-421087663a3c
ms.openlocfilehash: a4db1e21f344f5cc58e2027b0816f9c8fb40b3bc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519926"
---
# <a name="3110-ompgetnested-function"></a>3.1.10 Funkcja omp_get_nested

`omp_get_nested` Funkcja zwraca wartość różną od zera, jeśli włączono zagnieżdżonych równoległości i 0, jeśli jest ona wyłączona. Aby uzyskać więcej informacji na zagnieżdżonych równoległości sekcji 3.1.9 na stronie 40. Format jest następujący:

```
#include <omp.h>
int omp_get_nested(void);
```

Jeśli implementacja nie implementuje zagnieżdżonych równoległości, ta funkcja zawsze zwraca wartość 0.