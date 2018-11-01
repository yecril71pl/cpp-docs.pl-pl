---
title: 2.6.3 Dyrektywa określająca bariery
ms.date: 11/04/2016
ms.assetid: 4485a3d7-533f-4fec-8128-a131bec7fa16
ms.openlocfilehash: 9079dce4b2a27e91e349fd0df8414d38cd245d2e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637024"
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