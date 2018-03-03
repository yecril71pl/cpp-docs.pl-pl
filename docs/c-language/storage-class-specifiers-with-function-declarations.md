---
title: Specyfikatory klasy magazynowania z deklaracjami funkcji | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- function specifiers, storage class
- declaring functions, specifiers
- external declarations
- specifiers, function
- external linkage, function declarations
- external linkage, storage-class specifiers
ms.assetid: 801d7df2-efa9-4924-a725-274a5654cfd4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f7d8b6ba1c0287492195ee891b1a573bf74de6cf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="storage-class-specifiers-with-function-declarations"></a>Specyfikatory klasy magazynowania z deklaracjami funkcji
Możesz użyć dowolnej **statycznych** lub `extern` Specyfikator klasy magazynu w deklaracji funkcji. Funkcje zawsze mieć globalne okresy istnienia.  
  
 **Dotyczące firmy Microsoft**  
  
 Deklaracje funkcji na poziomie wewnętrznym ma takie samo znaczenie jak deklaracje funkcji na poziomie zewnętrznych. Oznacza to, że funkcja jest widoczna w punkcie deklaracji w dalszej części jednostce tłumaczenia, nawet wtedy, gdy jest ona zadeklarowana w zakresie lokalnym.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
 Reguły widoczności dla funkcji się nieco różnić od reguł dla zmiennych w następujący sposób:  
  
-   Funkcja zadeklarowana jako **statycznych** jest widoczna tylko w obrębie pliku źródłowego, w którym jest zdefiniowany. Można wywołać funkcji w tym samym pliku źródłowego **statycznych** funkcji, ale działa w innych plików źródłowych nie można uzyskać do niego dostęp bezpośrednio przez nazwę. Można zadeklarować innego **statycznych** funkcja o tej samej nazwie w pliku źródłowym różnych bez konfliktu.  
  
-   Funkcje deklarowane jako `extern` są widoczne w całym wszystkich plików źródłowych w programie (chyba że później ponownie zadeklarować funkcji jako **statycznych**). Dowolną funkcję można wywołać `extern` funkcji.  
  
-   Deklaracje funkcji, które pominąć specyfikator klasy magazynowania są `extern` domyślnie.  
  
 **Dotyczące firmy Microsoft**  
  
 Microsoft umożliwia ponowna definicja `extern` identyfikator **statycznych**.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy magazynu w języku C](../c-language/c-storage-classes.md)