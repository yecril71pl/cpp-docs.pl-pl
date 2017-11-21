---
title: Instrukcje iteracji (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- iteration statements
- loop structures, iteration statements
ms.assetid: bf6d75f7-ead2-426a-9c47-33847f59b8c7
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f81ffa2e6b8f1dc07e409b737f76cb8e6aca5258
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="iteration-statements-c"></a>Instrukcje iteracji (C++)
Iteracja — instrukcje spowodować instrukcji (lub instrukcje złożone) można wykonać zero lub więcej razy może ulec pewne kryteria zakończenia pętli. Jeśli te instrukcje są instrukcje złożone, są wykonywane w kolejności, chyba że albo [podziału](../cpp/break-statement-cpp.md) instrukcji lub [kontynuować](../cpp/continue-statement-cpp.md) napotkano instrukcji.  
  
 C++ udostępnia cztery instrukcje iteracji — [podczas](../cpp/while-statement-cpp.md), [czy](../cpp/do-while-statement-cpp.md), [dla](../cpp/for-statement-cpp.md), i [na podstawie zakresu dla](../cpp/range-based-for-statement-cpp.md). Każdy z tych iteracje do momentu jego zakończenia wyrażenie ma zero (FAŁSZ) lub do momentu zakończenia pętli jest wymuszone z **podziału** instrukcji. W poniższej tabeli przedstawiono te instrukcje i działań; Każdy została omówiona szczegółowo w kolejnych sekcjach.  
  
### <a name="iteration-statements"></a>Instrukcje iteracji  
  
|Instrukcja|Oceniane w|Inicjalizacja|Przyrost|  
|---------------|------------------|--------------------|---------------|  
|`while`|Początku pętli|Nie|Nie|  
|**czy**|Dołu pętli|Nie|Nie|  
|**dla**|Początku pętli|Tak|Tak|  
|**na podstawie zakresu dla**|Początku pętli|Tak|Tak|  
  
 Instrukcja część instrukcji iteracji nie może być deklaracji. Można go jednak instrukcji złożonej zawierającej deklaracji.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd instrukcji C++](../cpp/overview-of-cpp-statements.md)