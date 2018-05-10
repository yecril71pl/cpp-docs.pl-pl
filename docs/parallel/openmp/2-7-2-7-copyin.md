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
ms.openlocfilehash: 7ee711bfb24e7a2a1cbada1a7e01a243e204f4a8
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="2727-copyin"></a>2.7.2.7 kopiowanie
**Copyin** klauzuli zapewnia mechanizm można przypisać tę samą wartość na **threadprivate** zmienne dla każdego wątku w zespole wykonywania równoległego regionu. Dla każdej zmiennej określonej w **copyin** klauzuli, wartość zmiennej w głównym wątku zespołu jest kopiowany tak, jakby przez przypisanie do kopii prywatnego wątku na początku równoległego regionu. Składnia **copyin** klauzuli wygląda następująco:  
  
```  
  
copyin(  
variable-list  
)  
  
```  
  
 Ograniczenia do **copyin** klauzuli są następujące:  
  
-   Zmienna, która została określona w **copyin** klauzuli musi mieć operatora przypisania kopii dostępny, jednoznaczne.  
  
-   Zmienna, która została określona w **copyin** klauzuli musi być **threadprivate** zmiennej.