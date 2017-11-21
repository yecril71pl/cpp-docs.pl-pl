---
title: '&lt;scoped_allocator&gt; operatory | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- scoped_allocator/std::operator!=
- scoped_allocator/std::operator==
dev_langs: C++
ms.assetid: 4dfe0805-cc6e-479f-887f-a1c164f73837
caps.latest.revision: "10"
manager: ghogen
ms.openlocfilehash: d29a5a99f261776468364717a13b90a1ddde5216
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltscopedallocatorgt-operators"></a>&lt;scoped_allocator&gt; operatory
|||  
|-|-|  
|[operator! =](#op_neq)|[operator ==](#op_eq_eq)|  
  
##  <a name="op_neq"></a>operator! =  
 Sprawdza dwie `scoped_allocator_adaptor` obiekty pod kątem nierówności.  
  
```cpp  
template <class Outer, class... Inner>  
bool operator!=(
    const scoped_allocator_adaptor<Outer, Inner...>& left,  
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;  
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Po lewej stronie `scoped_allocator_adaptor` obiektu.  
  
 `right`  
 Prawo `scoped_allocator_adaptor` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `!(left == right)`  
  
##  <a name="op_eq_eq"></a>operator ==  
 Sprawdza dwie `scoped_allocator_adaptor` obiekty pod kątem równości.  
  
```cpp  
template <class Outer, class... Inner>  
bool operator==(
    const scoped_allocator_adaptor<Outer, Inner...>& left,  
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;  
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Po lewej stronie `scoped_allocator_adaptor` obiektu.  
  
 `right`  
 Prawo `scoped_allocator_adaptor` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `left.outer_allocator() == right.outer_allocator() && left.inner_allocator() == right.inner_allocator()`  
  
## <a name="see-also"></a>Zobacz też  
 [< scoped_allocator >](../standard-library/scoped-allocator.md)

