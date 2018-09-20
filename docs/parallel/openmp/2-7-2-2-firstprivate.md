---
title: 2.7.2.2 firstprivate | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: ece6ff12-2be1-4e4f-866c-d39345fd87b5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0d3e6ad966f4cf895da9374798f6c9a4079ccc2f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400968"
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