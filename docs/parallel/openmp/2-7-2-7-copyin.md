---
title: 2.7.2.7 copyin | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 76cfb9f8-bf65-4585-adbf-fd933f5606b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 94b4c529b7ad6fd717be1e1dee0edd3ff9ac3ff5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426890"
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