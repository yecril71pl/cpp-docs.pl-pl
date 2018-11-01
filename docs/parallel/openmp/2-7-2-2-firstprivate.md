---
title: 2.7.2.2 — firstprivate
ms.date: 11/04/2016
ms.assetid: ece6ff12-2be1-4e4f-866c-d39345fd87b5
ms.openlocfilehash: f981c66fd3e0a2f42dcf731954f5054f96ed2973
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605975"
---
# <a name="2722-firstprivate"></a>2.7.2.2 — firstprivate

**Firstprivate** klauzuli stanowi nadzbiór funkcje udostępniane przez **prywatnej** klauzuli. Składnia **firstprivate** klauzula jest w następujący sposób:

```
firstprivate(variable-list)
```

Zmienne określone w *liście zmiennych* mają **prywatnej** klauzuli semantykę, zgodnie z opisem w [sekcji 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) na stronie 25. Inicjowanie lub konstrukcji odbywa się tak, jakby były wykonywane raz na wątek przed wykonanie wątku konstrukcja. Aby uzyskać **firstprivate** klauzuli na konstrukcję równoległych, początkowa wartość nowego obiektu prywatnego jest wartością oryginalny obiekt, który występuje bezpośrednio przed równoległe konstrukcji dla wątku, który je napotka. Aby uzyskać **firstprivate** klauzuli w konstrukcji podziału pracy, początkowa wartość nowy obiekt prywatny dla każdego wątku, który jest wykonywany konstrukcji podziału pracy jest wartością oryginalny obiekt, który istnieje przed punkt w czasie, tym samym wątku napotyka konstrukcji podziału pracy. Ponadto dla obiektów C++, nowy obiekt prywatny dla każdego wątku jest kopia skonstruowany na podstawie oryginalnego obiektu.

Ograniczenia do **firstprivate** klauzuli są następujące:

- Określone w zmiennej **firstprivate** klauzuli nie może mieć typu niekompletnego lub typu odwołania.

- Zmiennej z typu klasy, która jest określona jako **firstprivate** musi mieć konstruktora kopiującego dostępny, jednoznaczną.

- Zmienne, które są prywatne w ramach równoległego regionu lub które są widoczne w **redukcji** klauzuli **równoległe** dyrektywy nie można określić w **firstprivate** klauzuli w dyrektywa podziału pracy, która jest powiązywana z konstrukcja równoległa.