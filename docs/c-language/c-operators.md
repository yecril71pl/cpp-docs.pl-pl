---
title: "Operatory języka C | Dokumentacja firmy Microsoft"
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
- ternary operators
- operators [C]
- symbols, operators
- binary operators
- associativity of operators
- binary data, binary expressions
ms.assetid: 13bc4c8e-2dc9-4b23-9f3a-25064e8777ed
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3d4acb0acec44d695bd4c03ffa102a0ac42971b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="c-operators"></a>Operatory języka C
Operatory języka C są podzbiorem [wbudowanych operatory C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md).  
  
 Istnieją trzy typy operatorów. Wyrażenie jednoargumentowe składa się z jednej dołączany na początku na operand operatora jednoargumentowego lub `sizeof` — słowo kluczowe wraz z wyrażeniem. Wyrażenie może być nazwą zmiennej lub wyrażeniem rzutowania. Jeśli wyrażenie jest wyrażeniem rzutowania, musi być ujęta w nawiasy. Wyrażenie binarne składa się z dwóch argumentów operacji dołączane za pomocą operatora binarnego. Wyrażenie trójargumentowy składa się z trzech argumentów operacji połączonych operator wyrażenia warunkowego.  
  
 C obejmuje następujące operatory jednoargumentowe:  
  
|Symbol|Nazwa|  
|------------|----------|  
|**- ~ !**|Operatory negacji i dopełnienia|  
|**\* &**|Operatory pośrednie i adresu|  
|`sizeof`|Size — operator|  
|**+**|Jednoargumentowe plus — operator|  
|**++ --**|Jednoargumentowy inkrementacji i dekrementacji operatorów|  
  
 Operatory binarne skojarzyć od lewej do prawej. C zapewnia następujące operatory binarne:  
  
|Symbol|Nazwa|  
|------------|----------|  
|**\* / %**|Operatory multiplikatywne|  
|**+ -**|Operatory addytywne|  
|**<\< >>**|Operatory przesunięcia|  
|**\<   >   \<=   >=   ==   !=**|Operatory relacyjne|  
|**&   &#124; ^**|Operatory bitowe|  
|**&&   &#124;&#124;**|Operatory logiczne|  
|**,**|Operator obliczania sekwencyjnego|  
  
 Podstawowa — operator (**: >**), obsługiwane przez poprzednie wersje kompilatora C Microsoft 16-bitowych, jest opisany w [podsumowanie dotyczące składni języka C](../c-language/c-language-syntax-summary.md).  
  
 Operator wyrażenia warunkowego ma niższy priorytet niż wyrażenia binarne i różni się od nich jest prawo asocjacyjnej.  
  
 Wyrażenia z operatorami także wyrażeń przypisania, które Użyj jednoargumentowego lub operatorów binarnych przypisania. Jednoargumentowe operatory przypisania są przyrostu (`++`) i dekrementacji (**--**) operatory; plik binarny operator przypisania prostego są operatory przypisania ( **=** ) i operatory przypisania złożone. Każdy operator przypisania złożone jest kombinacją innego operatora binarnego z operator przypisania prostego.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia i przydziały](../c-language/expressions-and-assignments.md)