---
title: "inplace_merge — (STL/CLR) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::inplace_merge
dev_langs:
- C++
helpviewer_keywords:
- inplace_merge function [STL/CLR]
ms.assetid: e6948c03-8c5b-4a7c-915c-0a531946a321
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6fbe1e70f17ac558da58b819c952e0f26026690c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="inplacemerge-stlclr"></a>inplace_merge (STL/CLR)
Łączy elementy z dwóch następujących po sobie posortowanych zakresów w pojedynczy posortowany zakres, gdzie kryterium szeregowania może być określone przez predykat binarny.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<class _BidIt> inline  
    void inplace_merge(_BidIt _First, _BidIt _Mid, _BidIt _Last);  
template<class _BidIt, class _Pr> inline  
    void inplace_merge(_BidIt _First, _BidIt _Mid, _BidIt _Last,  
        _Pr _Pred);  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `inplace_merge` uzyskać więcej informacji, zobacz [inplace_merge —](../standard-library/algorithm-functions.md#inplace_merge).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/algorytm >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)