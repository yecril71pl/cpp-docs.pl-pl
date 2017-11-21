---
title: "&lt;Pamięć&gt; wyliczenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
caps.latest.revision: "11"
manager: ghogen
ms.openlocfilehash: 52ccd226214da7ddbdca9c480bb2f8940203155e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltmemorygt-enums"></a>&lt;Pamięć&gt; wyliczenia
||  
|-|  
|[pointer_safety —](#pointer_safety)|  
  
##  <a name="pointer_safety"></a>pointer_safety — wyliczenie  
 Wyliczenia możliwych wartości zwracanych przez `get_pointer_safety`.  
  
pointer_safety — klasa, {swobodna, preferowane, ograniczeniami};  
  
### <a name="remarks"></a>Uwagi  
 Zakresie `enum` definiuje wartości, które mogą być zwrócone przez `get_pointer_safety()`:  
  
 `relaxed`--Wskaźniki nie bezpiecznie pochodnych (oczywiście wskaźników do obiektów zadeklarowane lub przydzielonego) są traktowane taki sam, jak te bezpiecznie pochodnych.  
  
 `preferred`--jak poprzednio, ale nie bezpiecznie pochodnych wskaźniki nie powinny wyłuskiwany.  
  
 `strict`--Wskaźniki nie bezpiecznie pochodnych może być traktowane inaczej niż te bezpiecznie pochodnych.  
  
## <a name="see-also"></a>Zobacz też  
 [\<pamięci >](../standard-library/memory.md)



