---
title: set_symmetric_difference — (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::set_symmetric_difference
dev_langs:
- C++
helpviewer_keywords:
- set_symmetric_difference function [STL/CLR]
ms.assetid: 4d8997c7-038e-42a8-86d4-81d714ed3775
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b5a0e4926c67671c6536ca39d949e7c97640cc11
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33162055"
---
# <a name="setsymmetricdifference-stlclr"></a>set_symmetric_difference (STL/CLR)
Łączy w sobie wszystkie elementy, które należą do jednego z, ale nie obu posortowanych zakresów źródłowych w pojedynczy posortowany zakres docelowy, gdzie kryterium szeregowania może być określone przez predykat binarny.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<class _InIt1, class _InIt2, class _OutIt> inline  
    _OutIt set_symmetric_difference(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);  
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline  
    _OutIt set_symmetric_difference(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `set_symmetric_difference`. Aby uzyskać więcej informacji, zobacz [set_symmetric_difference —](../standard-library/algorithm-functions.md#set_symmetric_difference).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/algorytm >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)