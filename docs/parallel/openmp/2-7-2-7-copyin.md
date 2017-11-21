---
title: 2.7.2.7 copyin | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 76cfb9f8-bf65-4585-adbf-fd933f5606b4
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cd296192146e76085e1b987e29a377eb621917ae
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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