---
title: "hash — Struktura (standardowa biblioteka C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: thread/std::hash
dev_langs: C++
ms.assetid: 4a8bf5bc-4334-4070-936b-98585f8a073b
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7625249f9d602d9c23daa36d067059bbe66fba34
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="hash-structure-c-standard-library"></a>hash — Struktura (standardowa biblioteka C++)
Definiuje funkcję elementu członkowskiego, która zwraca wartość, która unikatowo jest określany przez `Val`. Definiuje funkcję elementu członkowskiego [skrótu](../standard-library/hash-class.md) funkcji, które jest odpowiednie dla wartości mapowanie typu `thread::id` dystrybucji wartości indeksu.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <>  
struct hash<thread::id> :   
    public unary_function<thread::id, size_t>  
{  
    size_t operator()(thread::id Val) const;

 
};  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<wątku >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [\<Wątek >](../standard-library/thread.md)   
 [unary_function, struktura](../standard-library/unary-function-struct.md)
