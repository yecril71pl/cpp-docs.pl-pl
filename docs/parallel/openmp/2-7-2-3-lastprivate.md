---
title: 2.7.2.3 lastprivate | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 77f6a5c9-704f-4a88-8476-29db852ed800
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 25edca8391eb094691ef4fea3c360d351f979b43
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385966"
---
# <a name="2723-lastprivate"></a>2.7.2.3 ostatnia prywatna

`lastprivate` Klauzuli stanowi nadzbiór funkcje udostępniane przez `private` klauzuli. Składnia `lastprivate` klauzula jest w następujący sposób:

```
lastprivate(variable-list)
```

Zmienne określone w *liście zmiennych* mają `private` semantyki klauzuli. Gdy `lastprivate` klauzuli pojawia się na dyrektywę, który identyfikuje konstrukcji podziału pracy, wartość każdego `lastprivate` zmiennej z sekwencyjnie ostatniej iteracji pętli skojarzone lub leksykalnie ostatnią dyrektywą sekcji, jest przypisany do oryginalny obiekt w zmiennej. Zmienne, które nie są przypisane wartości w ostatniej iteracji **dla** lub **równoległe w**, lub przez leksykalnie ostatnią sekcję **sekcje** lub  **sekcji równoległych** dyrektywy, mają wartości nieokreślone po konstrukcji. Nieprzypisane podobiektów również mieć nieokreślona wartość po konstrukcji.

Ograniczenia do `lastprivate` klauzuli są następujące:

- Wszystkie ograniczenia dla `private` zastosowania.

- Zmiennej z typu klasy, która jest określona jako `lastprivate` musi być dostępny, jednoznaczną kopia operatora przypisania.

- Zmienne, które są prywatne w ramach równoległego regionu lub które są widoczne w `reduction` klauzuli **równoległe** dyrektywy nie można określić w `lastprivate` klauzuli w dyrektywie podziału pracy, która jest powiązywana z konstrukcja równoległa.