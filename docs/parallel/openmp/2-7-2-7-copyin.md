---
title: 2.7.2.7 kopiowanie
ms.date: 11/04/2016
ms.assetid: 76cfb9f8-bf65-4585-adbf-fd933f5606b4
ms.openlocfilehash: 20db32530ee60967245497cdfb12a0fce103f7b7
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519532"
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