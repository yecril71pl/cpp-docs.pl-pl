---
title: "unchecked_array_iterator — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: stdext::unchecked_array_iterator
dev_langs: C++
ms.assetid: 693b3b30-4e3a-465b-be06-409700bc50b1
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 82c040c4d3e773809d2202c553206e5c98f132db
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="uncheckedarrayiterator-class"></a>unchecked_array_iterator — Klasa
`unchecked_array_iterator` Klasa umożliwia zawijać tablicy lub wskaźnika do iteratora niezaznaczone. Klasa jest używana jako otoka (przy użyciu [make_unchecked_array_iterator](../standard-library/iterator-functions.md#make_unchecked_array_iterator) funkcji) dla wskaźników raw lub tablic jako docelowych sposób zarządzania ostrzeżenia wskaźnika niezaznaczone zamiast globalnie wykluczania tych ostrzeżeń. Jeśli to możliwe, preferowane sprawdzona wersja tej klasy [checked_array_iterator —](../standard-library/checked-array-iterator-class.md).  
  
> [!NOTE]
>  Ta klasa jest rozszerzeniem Microsoft standardowej biblioteki C++. Kod zaimplementowany przy użyciu tej funkcji nie jest przenośny do standardowych środowisk kompilacji C++, które nie obsługują tego rozszerzenia Microsoft.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Iterator>  
class unchecked_array_iterator;
```  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa jest zdefiniowana w [stdext —](../standard-library/stdext-namespace.md) przestrzeni nazw.  
  
 To jest wersja niezaznaczone [checked_array_iterator — klasa](../standard-library/checked-array-iterator-class.md) i obsługuje te same przeciążenia i elementów członkowskich. Aby uzyskać więcej informacji, funkcja iteratora zaznaczone z przykładów kodu, zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<iteratora >  
  
 **Namespace:** stdext —  
  
## <a name="see-also"></a>Zobacz też  
 [\<Iterator >](../standard-library/iterator.md)   
 [Odwołanie do biblioteki C++ Standard](../standard-library/cpp-standard-library-reference.md)



