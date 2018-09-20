---
title: 2.6.3 dyrektywa określająca bariery | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 4485a3d7-533f-4fec-8128-a131bec7fa16
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8654534143e6feed06e93406c8fe03983ee9c2fc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429152"
---
# <a name="263-barrier-directive"></a>2.6.3 Dyrektywa określająca bariery

**Barierę** dyrektywy synchronizuje wszystkie wątki w zespole. W przypadku każdego wątku w zespole czeka, aż wszystkie pozostałe on osiągnąć tego punktu. Składnia **barierę** dyrektywy jest następująca:

```
#pragma omp barrier new-line
```

Po wszystkie wątki w zespole wystąpił barierę, rozpoczyna się każdy wątek w zespole, wykonywania instrukcji po dyrektywie barierę równolegle. Należy pamiętać, że ponieważ **barierę** dyrektywy, nie ma instrukcji języka C w ramach jego składni, istnieją pewne ograniczenia dotyczące jego położenie w obrębie programu. Zobacz [dodatku C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md) dla formalnych gramatyki. W poniższym przykładzie przedstawiono te ograniczenia.

```
/* ERROR - The barrier directive cannot be the immediate
*          substatement of an if statement
*/
if (x!=0)
   #pragma omp barrier
...

/* OK - The barrier directive is enclosed in a
*      compound statement.
*/
if (x!=0) {
   #pragma omp barrier
}
```