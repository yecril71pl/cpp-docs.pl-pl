---
title: "output_iterator_tag — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xutility/std::output_iterator_tag
dev_langs: C++
helpviewer_keywords:
- output_iterator_tag class
- output_iterator_tag struct
ms.assetid: c23a4331-b069-4fa0-9c3a-1c9be7095553
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3558e8169d2facdd7319635c852847e3dc77c7ad
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="outputiteratortag-struct"></a>output_iterator_tag — Struktura
Klasa, która zawiera typ zwracany dla **iterator_category** funkcja, która reprezentuje iteratora danych wyjściowych.  
  
## <a name="syntax"></a>Składnia  
  
{} output_iterator_tag — struktura;  
  
## <a name="remarks"></a>Uwagi  
 Klasy tag kategorii są używane jako kompilacji znaczników dla algorytmu zaznaczenia. Funkcja szablonu musi znaleźć najbardziej określonej kategorii argumentu iteratora tak, aby najbardziej efektywny algorytm może użyć w czasie kompilacji. Dla każdego iteratora typu `Iterator`, `iterator_traits` <  `Iterator` >  **:: iterator_category** musi być zdefiniowany jako najbardziej konkretny tag kategorii, który określa zachowanie iteratora.  
  
 Typ jest taki sam jak **iterator** \< **Iter**> **:: iterator_category** podczas **Iter** opisuje obiekt, który może służyć jako iterator danych wyjściowych.  
  
 Ten tag nie jest sparametryzowana na `value_type` lub `difference_type` dla iteratora, podobnie jak w przypadku innych tagów iteratora, ponieważ dane wyjściowe Iteratory nie mają albo `value_type` lub `difference_type`.  
  
## <a name="example"></a>Przykład  
 Zobacz [iterator_traits](../standard-library/iterator-traits-struct.md) lub [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md) przykład sposobu użycia **iterator_tag**s.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<iteratora >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Odwołanie do biblioteki C++ Standard](../standard-library/cpp-standard-library-reference.md)



