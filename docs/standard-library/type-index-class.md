---
title: "type_index — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: typeindex/std::type_index
dev_langs: C++
helpviewer_keywords: type_index class
ms.assetid: db366119-74cb-43e8-aacf-9679e561fa2f
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b4b55118f4138da60a0b4a197b6ecc3f818441a0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="typeindex-class"></a>type_index — Klasa
`type_index` Klasy opakowuje wskaźnik do [type_info — klasa](../cpp/type-info-class.md) ułatwiających indeksowania przez takie obiekty.  
  
type_index — klasa {publicznego: type_index — (const type_info — & tinfo); Stała *name() char const; size_t hash_code() const bool — operator == (const type_info — & prawej) const; bool — operator! = (const type_info — & prawej) const; bool operator <(const type_ informacje o & prawej) const; bool — operator\<= (const type_info — & prawej) const; bool — operator > (const type_info — & prawej) const; bool — operator > = (const type_info — & prawej) const;};  
  
 Konstruktor inicjuje `ptr` do `&tinfo`.  
  
 `name`Zwraca `ptr->name()`.  
  
 `hash_code`Zwraca`ptr->hash_code().`  
  
 `operator==`Zwraca `*ptr == right.ptr`.  
  
 `operator!=`Zwraca `!(*this == right)`.  
  
 `operator<`Zwraca `*ptr->before(*right.ptr)`.  
  
 `operator<=`Zwraca`!(right < *this).`  
  
 `operator>`Zwraca `right < *this`.  
  
 `operator>=`Zwraca `!(*this < right)`.  
  
## <a name="see-also"></a>Zobacz też  
 [Informacje typu Run-Time](../cpp/run-time-type-information.md)   
 [\<typeindex >](../standard-library/typeindex.md)



