---
title: "&lt;sstream —&gt; funkcje | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sstream/std::swap
ms.assetid: bc9607e8-7c6b-44ef-949b-19e917b450ad
caps.latest.revision: "10"
manager: ghogen
ms.openlocfilehash: dfa71e79d801fbe48f55b81ae4189cdd6d977afe
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltsstreamgt-functions"></a>&lt;sstream —&gt; funkcji
||  
|-|  
|[swap](#sstream_swap)|  
  
##  <a name="sstream_swap"></a>swap  
 Zamienia wartości między dwoma `sstream` obiektów.  
  
```  
template <class Elem, class Tr, class Alloc>  
void swap(
    basic_stringbuf<Elem, Tr, Alloc>& left,  
    basic_stringbuf<Elem, Tr, Alloc>& right);

template <class Elem, class Tr, class Alloc>  
void swap(
    basic_istringstream<Elem, Tr, Alloc>& left,  
    basic_istringstream<Elem, Tr, Alloc>& right);

template <class Elem, class Tr, class Alloc>  
void swap(
    basic_ostringstream<Elem, Tr, Alloc>& left,  
    basic_ostringstream<Elem, Tr, Alloc>& right);

template <class Elem, class Tr, class Alloc>  
void swap(
    basic_stringstream<Elem, Tr, Alloc>& left,  
    basic_stringstream<Elem, Tr, Alloc>& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`left`|Odwołanie do `sstream` obiektu.|  
|`right`|Odwołanie do `sstream` obiektu.|  
  
### <a name="remarks"></a>Uwagi  
 Funkcja szablonu wykonuje `left.swap(right)`.  
  
## <a name="see-also"></a>Zobacz też  
 [\<sstream — >](../standard-library/sstream.md)

