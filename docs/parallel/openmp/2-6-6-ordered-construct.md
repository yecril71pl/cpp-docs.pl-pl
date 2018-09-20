---
title: 2.6.6 konstrukcja uporządkowana | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5b3c1ba5-cfb8-4b05-865b-f446ae1c9f7c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7b83c3dfc13b231a1314343a1dff496acf7a99b6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412200"
---
# <a name="266-ordered-construct"></a>2.6.6 Konstrukcja uporządkowana

Następujący blok strukturalny **uporządkowane** dyrektywa jest wykonywany w kolejności, w którym będzie można wykonywać iteracje, w pętli sekwencyjnej. Składnia **uporządkowane** dyrektywy jest następująca:

```
#pragma omp ordered new-linestructured-block
```

**Uporządkowane** dyrektywy musi należeć do zakresu dynamicznego **dla** lub **równoległe w** konstruowania. **Dla** lub **równoległe w** dyrektywy, do którego **uporządkowane** powiązań konstrukcja musi mieć **uporządkowane** klauzulę zgodnie z opisem w temacie [Sekcji 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) na stronie 11. W trakcie wykonania **dla** lub **równoległe w** skonstruować przy użyciu **uporządkowane** klauzuli **uporządkowane** konstrukcji są wykonywane wyłącznie w kolejność, w którym będzie można wykonywać w wykonanie sekwencyjne pętli.

Ograniczenia **uporządkowane** dyrektywy jest następująca:

- Iteracji pętli za pomocą **dla** konstrukcja nie musi wykonać uporządkowane dyrektywa więcej niż jeden raz i nie musisz wykonać więcej niż jedną **uporządkowane** dyrektywy.