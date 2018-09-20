---
title: 2.6.5 dyrektywa opróżniania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a2ec5f74-9c37-424a-8376-47ab4a5829a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d67453b636d50fcb78092318ebb76f5192817548
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442737"
---
# <a name="265-flush-directive"></a>2.6.5 Dyrektywa opróżniania

**Opróżniania** dyrektywy, czy jawnych ani dorozumianych, określa punktu sekwencji "międzywątkowe" jaką wdrożenia jest wymagany do upewnij się, że wszystkie wątki w zespole spójny widok niektórych obiektów (wymienionymi poniżej) w ilość pamięci. Oznacza to, że spełniono poprzednie wersje ewaluacyjne wyrażeń, które odwołują się do tych obiektów, a kolejne oceny jeszcze nie zostały rozpoczęte. Na przykład kompilatory należy przywrócić wartości obiektów z rejestrów w pamięci i sprzętu może być konieczne opróżnienia buforów zapisu w pamięci i ponownie załaduj wartości obiektów z pamięci.

Składnia **opróżniania** dyrektywy jest następująca:

```
#pragma omp flush [(variable-list)]  new-line
```

Jeśli obiekty, które wymagają synchronizacji mogą wszystkie zostać wyznaczony przez zmienne, a następnie tych zmiennych można określić opcjonalny *liście zmiennych*. Jeśli wskaźnik jest obecny w *liście zmiennych*, wskaźnika, sama jest opróżniany, nie obiekt wskaźnika odwołuje się do.

A **opróżniania** dyrektywy bez *liście zmiennych* synchronizuje wszystkich udostępnionych obiektów, z wyjątkiem niedostępnych obiektów z automatycznym okresem magazynu. (Jest to prawdopodobnie mają większe obciążenie niż **opróżniania** z *liście zmiennych*.) A **opróżniania** dyrektywy bez *liście zmiennych* jest implikowane dla następujących dyrektywach:

- `barrier`

- Wpis i wyjścia z **krytyczne**

- Wpis i wyjścia z `ordered`

- Wpis i wyjścia z **równoległe**

- At zakończenia z **dla**

- At zakończenia z **sekcje**

- At zakończenia z **pojedynczego**

- Wpis i wyjścia z **równoległe w**

- Wpis i wyjścia z **sekcji równoległych**

Jeśli dyrektywa nie jest implikowana `nowait` klauzula jest obecny. Należy zauważyć, że **opróżniania** dyrektywy nie jest implikowana dla żadnego z następujących czynności:

- Na wpis **dla**

- Wpis do lub wyjście z **master**

- Na wpis **sekcje**

- Na wpis **pojedynczego**

Odwołania, który uzyskuje dostęp do wartości obiektu z typem kwalifikowana volatile zachowuje się jak w przypadku **opróżniania** dyrektywy określenie tego obiektu w poprzednim punkcie sekwencji. Odwołania, która modyfikuje wartość obiektu o typie kwalifikowana volatile zachowuje się jak w przypadku **opróżniania** dyrektywy określenie tego obiektu w momencie kolejnych sekwencji.

Należy pamiętać, że ponieważ **opróżniania** dyrektywy, nie ma instrukcji języka C w ramach jego składni, istnieją pewne ograniczenia dotyczące jego położenie w obrębie programu. Zobacz [dodatku C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md) dla formalnych gramatyki. W poniższym przykładzie przedstawiono te ograniczenia.

```
/* ERROR - The flush directive cannot be the immediate
*          substatement of an if statement.
*/
if (x!=0)
   #pragma omp flush (x)
...

/* OK - The flush directive is enclosed in a
*      compound statement
*/
if (x!=0) {
   #pragma omp flush (x)
}
```

Ograniczenia **opróżniania** dyrektywy jest następująca:

- Określone w zmiennej **opróżniania** dyrektywy nie może mieć typu referencyjnego.