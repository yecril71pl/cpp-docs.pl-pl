---
title: 2.7.2.3 ostatnia prywatna
ms.date: 11/04/2016
ms.assetid: 77f6a5c9-704f-4a88-8476-29db852ed800
ms.openlocfilehash: 15f9af23c4f4e1c0ce2914a979f7a41e7b4a6bc1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428463"
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