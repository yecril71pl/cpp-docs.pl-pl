---
title: obejmuje (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::includes
dev_langs: C++
helpviewer_keywords: includes function [STL/CLR]
ms.assetid: 566307f4-92e0-4acc-ba49-caa48f3ec744
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 94ba313a960b986412a5fc41293b0770ace01211
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="includes-stlclr"></a>includes (STL/CLR)
Sprawdza, czy jeden posortowany zakres zawiera wszystkie elementy zawarte w drugim posortowanym zakresie, gdzie kryterium szeregowania lub równoważności między elementami może zostać określone przez predykat binarny.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<class _InIt1, class _InIt2> inline  
    bool includes(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2);  
template<class _InIt1, class _InIt2, class _Pr> inline  
    bool includes(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `includes`. Aby uzyskać więcej informacji, zobacz [obejmuje](../standard-library/algorithm-functions.md#includes).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/algorytm >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)