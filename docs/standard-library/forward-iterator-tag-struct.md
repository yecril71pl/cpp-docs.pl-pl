---
title: "forward_iterator_tag — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xutility/std::forward_iterator_tag
dev_langs: C++
helpviewer_keywords:
- forward_iterator_tag struct
- forward_iterator_tag class
ms.assetid: 68b633ac-b135-4e9e-837d-14248a262ec5
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2a6d48940faf4645421a863411058ebfce1949aa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="forwarditeratortag-struct"></a>forward_iterator_tag — Struktura
Klasa, która zawiera typ zwracany dla **iterator_category** funkcja, która reprezentuje iteratora do przodu.  
  
## <a name="syntax"></a>Składnia  
  
```
struct forward_iterator_tag    : public input_iterator_tag {};
```  
  
## <a name="remarks"></a>Uwagi  
 Klasy tag kategorii są używane jako kompilacji znaczników dla algorytmu zaznaczenia. Funkcja szablonu należy dowiedzieć się, co to jest najbardziej określonej kategorii argumentu iteratora tak, aby najbardziej efektywny algorytm może użyć w czasie kompilacji. Dla każdego iteratora typu `Iterator`, `iterator_traits` <  `Iterator` >  **:: iterator_category** musi być zdefiniowany jako najbardziej konkretny tag kategorii, który określa zachowanie iteratora.  
  
 Typ jest taki sam jak **iterator** \< **Iter**> **:: iterator_category** podczas **Iter** opisuje obiekt, który może służyć jako iterator do przodu.  
  
## <a name="example"></a>Przykład  
 Zobacz [iterator_traits](../standard-library/iterator-traits-struct.md) lub [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md) przykład sposobu użycia **iterator_tag**s.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<iteratora >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [input_iterator_tag — struktura](../standard-library/input-iterator-tag-struct.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Odwołanie do biblioteki C++ Standard](../standard-library/cpp-standard-library-reference.md)



