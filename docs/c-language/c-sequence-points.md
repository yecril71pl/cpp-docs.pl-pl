---
title: "Punkty sekwencji języka C | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: sequence points
ms.assetid: c84885a5-4336-4eba-a643-058df4249903
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f86bd3feacbabdd11d6c8ec04b4aec96ec2f5e1a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="c-sequence-points"></a>Punkty sekwencji języka C
Między kolejnymi "punkty sekwencji" wartość obiektu można modyfikować tylko raz przez wyrażenie. Język C definiuje następujące punkty sekwencji:  
  
-   Lewej strony logicznej- i — operator (**&&**). Lewy argument operacji logicznych-operator całkowicie jest obliczane i wszystkie efekty uboczne zakończenie przed kontynuowaniem. Argument operacji nie jest oceniany, jeśli Lewy argument operacji daje w wyniku wartość false (0).  
  
-   Lewej strony operatora logicznego OR (`||`). Lewy argument operacji operatora logicznego OR całkowicie jest obliczane i wszystkie efekty uboczne zakończenie przed kontynuowaniem. Argument operacji nie jest oceniany, jeśli Lewy argument operacji daje w wyniku wartość true (różną od zera).  
  
-   Lewy operand operatora przecinka. Lewy argument operacji operatora przecinka całkowicie jest obliczane i wszystkie efekty uboczne zakończenie przed kontynuowaniem. Oba operandy operatora przecinka są obliczane zawsze. Należy pamiętać, że operatora przecinka w wywołaniu funkcji nie gwarantuje kolejność obliczania.  
  
-   Operator wywołania funkcji. Wszystkie argumenty funkcji są oceniane i wszystkie efekty uboczne ukończyć przed wejściem do funkcji. Nie kolejność obliczania między argumenty został określony.  
  
-   Pierwszy operand operatora warunkowego. Pierwszy argument operacji operatora warunkowego całkowicie jest obliczane i wszystkie efekty uboczne zakończenie przed kontynuowaniem.  
  
-   Koniec wyrażenia pełnej inicjalizacji (to znaczy wyrażenie, które nie jest częścią innego wyrażenia, takich jak koniec Inicjalizacja w instrukcji deklaracji).  
  
-   Wyrażenie w instrukcji wyrażenia. Instrukcje wyrażeń składają się z opcjonalne wyrażenie następuje średnik (**;**). Wyrażenie jest obliczane dla jej efekty uboczne i ma punktu sekwencji po dokonaniu oceny.  
  
-   Kontrolowanie wyrażenie w wyborze (**Jeśli** lub `switch`) instrukcji. Wyrażenie całkowicie jest obliczane i wszystkie efekty uboczne ukończenie wykonywany jest kod zależna od zaznaczenia.  
  
-   Kontrolowanie wyrażenie `while` lub **czy** instrukcji. Wyrażenie całkowicie jest obliczane i wszystkie efekty uboczne ukończona przed wszystkimi instrukcjami w następnej iteracji `while` lub **czy** pętli są wykonywane.  
  
-   Każdy z trzech wyrażeń **dla** instrukcji. Wyrażenia całkowicie są przetwarzane i wszystkie efekty uboczne ukończona przed wszystkimi instrukcjami w następnej iteracji **dla** pętli są wykonywane.  
  
-   Wyrażenie w `return` instrukcji. Wyrażenie całkowicie jest obliczane i wszystkie efekty uboczne ukończenie kontroli zwraca wywołania funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Szacowanie wyrażeń](../c-language/expression-evaluation-c.md)