---
title: 2.6.6 Konstrukcja uporządkowana
ms.date: 11/04/2016
ms.assetid: 5b3c1ba5-cfb8-4b05-865b-f446ae1c9f7c
ms.openlocfilehash: fe6ad4adf2a4fcccfefe3c3585d9c88c0a118931
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615803"
---
# <a name="266-ordered-construct"></a>2.6.6 Konstrukcja uporządkowana

Następujący blok strukturalny **uporządkowane** dyrektywa jest wykonywany w kolejności, w którym będzie można wykonywać iteracje, w pętli sekwencyjnej. Składnia **uporządkowane** dyrektywy jest następująca:

```
#pragma omp ordered new-linestructured-block
```

**Uporządkowane** dyrektywy musi należeć do zakresu dynamicznego **dla** lub **równoległe w** konstruowania. **Dla** lub **równoległe w** dyrektywy, do którego **uporządkowane** powiązań konstrukcja musi mieć **uporządkowane** klauzulę zgodnie z opisem w temacie [Sekcji 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) na stronie 11. W trakcie wykonania **dla** lub **równoległe w** skonstruować przy użyciu **uporządkowane** klauzuli **uporządkowane** konstrukcji są wykonywane wyłącznie w kolejność, w którym będzie można wykonywać w wykonanie sekwencyjne pętli.

Ograniczenia **uporządkowane** dyrektywy jest następująca:

- Iteracji pętli za pomocą **dla** konstrukcja nie musi wykonać uporządkowane dyrektywa więcej niż jeden raz i nie musisz wykonać więcej niż jedną **uporządkowane** dyrektywy.