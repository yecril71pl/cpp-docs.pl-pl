---
title: A.1 wykonywanie równoległe prostej pętli | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b8aaacae-b20d-4b16-a540-54ccbf09582b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b5446f72cc5ee0577385527be24bc912297aec0d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418948"
---
# <a name="a1---executing-a-simple-loop-in-parallel"></a>A.1   Wykonywanie równoległe prostej pętli

Poniższy przykład pokazuje, jak zrównoleglić przy użyciu prostej pętli `parallel for` — dyrektywa ([sekcji 2.5.1](../../parallel/openmp/2-5-1-parallel-for-construct.md) na stronie 16). Zmienna iteracji pętli jest domyślnie prywatny, więc nie jawnie określ wartość w klauzuli prywatnej.

```
#pragma omp parallel for
    for (i=1; i<n; i++)
        b[i] = (a[i] + a[i-1]) / 2.0;
```