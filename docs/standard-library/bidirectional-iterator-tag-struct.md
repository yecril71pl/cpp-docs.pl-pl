---
title: "bidirectional_iterator_tag — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xutility/std::bidirectional_iterator_tag
dev_langs: C++
helpviewer_keywords:
- bidirectional_iterator_tag class
- bidirectional_iterator_tag struct
ms.assetid: 9ac06066-b8ae-44b6-bee4-b05855f6a31a
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6ac5f22a22ad64e137a56be964068229a6ed0958
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="bidirectionaliteratortag-struct"></a>bidirectional_iterator_tag — Struktura
Klasa, która zawiera typ zwracany dla **iterator_category** funkcja, która reprezentuje iteratora dwukierunkowego.  
  
## <a name="syntax"></a>Składnia  
  
```
struct bidirectional_iterator_tag    : public forward_iterator_tag {};
```  
  
## <a name="remarks"></a>Uwagi  
 Klasy tag kategorii są używane jako kompilacji znaczników dla algorytmu zaznaczenia. Funkcja szablonu musi znaleźć najbardziej określonej kategorii argumentu iteratora, dzięki czemu najbardziej efektywny algorytm może użyć w czasie kompilacji. Dla każdego iteratora typu `Iterator`, `iterator_traits` <  `Iterator`>:: **iterator_category** musi być zdefiniowany jako najbardziej konkretny tag kategorii, który określa zachowanie iteratora.  
  
 Typ jest taki sam jak **iterator** \< **Iter**>:: **iterator_category** podczas **Iter** opisuje obiekt, który można służyć jako iterator dwukierunkowego.  
  
## <a name="example"></a>Przykład  
 Zobacz [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md) przykład sposobu użycia `bidirectional_iterator_tag`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<iteratora >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [forward_iterator_tag — struktura](../standard-library/forward-iterator-tag-struct.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)



