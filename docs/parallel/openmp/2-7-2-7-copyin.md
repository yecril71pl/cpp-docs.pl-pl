---
title: 2.7.2.7 kopiowanie
ms.date: 11/04/2016
ms.assetid: 76cfb9f8-bf65-4585-adbf-fd933f5606b4
ms.openlocfilehash: 65bb8faba085e5582e779fa0e9d5bf1a91a39f0e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545447"
---
# <a name="2727-copyin"></a>2.7.2.7 kopiowanie

**Copyin** klauzuli zapewnia mechanizm, aby przypisać tę samą wartość, aby **threadprivate** zmienne dla każdego wątku w zespole wykonywania równoległego regionu. Dla każdej zmiennej, określone w **copyin** klauzuli, wartość zmiennej w głównym wątku zespołu, jest kopiowany, tak, jakby przez przypisanie do kopii prywatnego wątku na początku równoległego regionu. Składnia **copyin** klauzula jest w następujący sposób:

```

copyin(
variable-list
)

```

Ograniczenia do **copyin** klauzuli są następujące:

- Zmienna, która została określona w **copyin** klauzula musi mieć operatora przypisania kopiowania dostępny, jednoznaczną.

- Zmienna, która została określona w **copyin** musi mieć klauzulę **threadprivate** zmiennej.