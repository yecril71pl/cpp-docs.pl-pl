---
title: 2.7.2.1 — prywatny
ms.date: 11/04/2016
ms.assetid: 079b4b84-f2b3-4050-a0ac-289493c36b3d
ms.openlocfilehash: c1a2560eb80c848605698c435e3a0f0f7e66b75a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536958"
---
# <a name="2721-private"></a>2.7.2.1 — prywatny

`private` Klauzuli deklarujemy zmienne na liście zmiennych można używać prywatnego każdy wątek w zespole. Składnia `private` klauzula jest w następujący sposób:

```
private(variable-list)
```

Zachowanie określone w zmiennej `private` klauzula jest w następujący sposób. Nowy obiekt z automatycznym okresem magazynu jest przydzielany dla konstrukcji. Rozmiar i wyrównanie nowego obiektu są określane przez typ zmiennej. Ten przydział wykonywana jeden raz dla każdego wątku w zespole, a domyślny konstruktor jest wywoływana dla obiektu klasy, w razie potrzeby; w przeciwnym razie wartość początkowa jest nieokreślony.  Oryginalny obiekt odwołuje się zmienna ma nieokreśloną wartość po wejściu do konstrukcja nie mogą zostać zmodyfikowane w ramach zakresu dynamiczna konstrukcja i ma nieokreśloną wartość przy zamykaniu z konstrukcja.

W zakresie leksykalnym dyrektywy konstrukcji zmienna odwołuje się do nowego obiektu prywatnej przydzielonej przez wątek.

Ograniczenia do `private` klauzuli są następujące:

- Zmiennej z typu klasy, która została określona w `private` klauzuli musi mieć dostęp, jednoznaczną domyślnego konstruktora.

- Określone w zmiennej `private` nie mogą zawierać klauzuli **const**-wykwalifikowany typ, chyba że jego klasa to typ `mutable` elementu członkowskiego.

- Określone w zmiennej `private` klauzuli nie może mieć typu niekompletnego lub typu odwołania.

- Zmienne, które pojawiają się w `reduction` klauzuli **równoległe** dyrektywy nie można określić w `private` klauzuli w dyrektywie podziału pracy, która jest powiązywana z konstrukcja równoległa.