---
title: Specyfikatory klasy magazynowania z deklaracjami funkcji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f84455dd29023194e64fa4e594419630ef2656e6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="storage-class-specifiers-with-function-declarations"></a>Specyfikatory klasy magazynowania z deklaracjami funkcji
Możesz użyć dowolnej **statycznych** lub `extern` Specyfikator klasy magazynu w deklaracji funkcji. Funkcje zawsze mieć globalne okresy istnienia.  
  
 **Microsoft Specific**  
  
 Deklaracje funkcji na poziomie wewnętrznym ma takie samo znaczenie jak deklaracje funkcji na poziomie zewnętrznych. Oznacza to, że funkcja jest widoczna w punkcie deklaracji w dalszej części jednostce tłumaczenia, nawet wtedy, gdy jest ona zadeklarowana w zakresie lokalnym.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
 Reguły widoczności dla funkcji się nieco różnić od reguł dla zmiennych w następujący sposób:  
  
-   Funkcja zadeklarowana jako **statycznych** jest widoczna tylko w obrębie pliku źródłowego, w którym jest zdefiniowany. Można wywołać funkcji w tym samym pliku źródłowego **statycznych** funkcji, ale działa w innych plików źródłowych nie można uzyskać do niego dostęp bezpośrednio przez nazwę. Można zadeklarować innego **statycznych** funkcja o tej samej nazwie w pliku źródłowym różnych bez konfliktu.  
  
-   Funkcje deklarowane jako `extern` są widoczne w całym wszystkich plików źródłowych w programie (chyba że później ponownie zadeklarować funkcji jako **statycznych**). Dowolną funkcję można wywołać `extern` funkcji.  
  
-   Deklaracje funkcji, które pominąć specyfikator klasy magazynowania są `extern` domyślnie.  
  
 **Microsoft Specific**  
  
 Microsoft umożliwia ponowna definicja `extern` identyfikator **statycznych**.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy magazynu w języku C](../c-language/c-storage-classes.md)