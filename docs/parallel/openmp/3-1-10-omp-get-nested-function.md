---
title: 3.1.10 funkcja omp_get_nested | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 48736a25-5c6e-4e2d-aad0-421087663a3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d019dd757080bbc87ff7aaab1a8745b2a3156b39
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392284"
---
# <a name="3110-ompgetnested-function"></a>3.1.10 Funkcja omp_get_nested

`omp_get_nested` Funkcja zwraca wartość różną od zera, jeśli włączono zagnieżdżonych równoległości i 0, jeśli jest ona wyłączona. Aby uzyskać więcej informacji na zagnieżdżonych równoległości sekcji 3.1.9 na stronie 40. Format jest następujący:

```
#include <omp.h>
int omp_get_nested(void);
```

Jeśli implementacja nie implementuje zagnieżdżonych równoległości, ta funkcja zawsze zwraca wartość 0.