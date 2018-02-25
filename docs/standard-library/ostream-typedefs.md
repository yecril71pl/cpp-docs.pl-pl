---
title: "&lt;ostream&gt; definicje typów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
caps.latest.revision: 
manager: ghogen
ms.openlocfilehash: c9ab11cf6436888605a07c91051bf27c45e10fcf
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt; definicje typów
|||  
|-|-|  
|[ostream](#ostream)|[wostream](#wostream)|  
  
##  <a name="ostream"></a>  ostream  
 Tworzy typ na podstawie basic_ostream —, które jest przeznaczone na `char` i `char_traits` specjalne na `char`.  
  
```
typedef basic_ostream<char, char_traits<char>> ostream;
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem dla szablonu klasy [basic_ostream —](../standard-library/basic-ostream-class.md), wyspecjalizowany dla elementów typu `char` z domyślnego cech znaków.  
  
##  <a name="wostream"></a>  wostream  
 Tworzy typ na podstawie basic_ostream —, które jest przeznaczone na `wchar_t` i `char_traits` specjalne na `wchar_t`.  
  
```
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem dla szablonu klasy [basic_ostream —](../standard-library/basic-ostream-class.md), wyspecjalizowany dla elementów typu `wchar_t` z domyślnego cech znaków.  
  
## <a name="see-also"></a>Zobacz też  
 [\<ostream>](../standard-library/ostream.md)



