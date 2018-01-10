---
title: remove_copy_if (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::remove_copy_if
dev_langs: C++
helpviewer_keywords: remove_copy_if function [STL/CLR]
ms.assetid: 5307f5fe-b6bb-4968-8da1-fea84ab96655
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 11e4b7086e9e61f6ac04edc06e8f86ddf7dc849b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="removecopyif-stlclr"></a>remove_copy_if (STL/CLR)
Kopiuje elementy z zakresu źródłowego do zakresu docelowego, z tym wyjątkiem, że elementy spełniające predykat nie są kopiowane, bez naruszania kolejności pozostałych elementów i zwracania końca nowego zakresu docelowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<class _InIt, class _OutIt, class _Pr> inline  
    _OutIt remove_copy_if(_InIt _First, _InIt _Last, _OutIt _Dest,  
        _Pr _Pred);  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `remove_copy_if`. Aby uzyskać więcej informacji, zobacz [remove_copy_if](../standard-library/algorithm-functions.md#remove_copy_if).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/algorytm >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)