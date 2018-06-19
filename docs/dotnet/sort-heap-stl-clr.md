---
title: sort_heap — (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::sort_heap
dev_langs:
- C++
helpviewer_keywords:
- sort_heap function [STL/CLR]
ms.assetid: a8fa6b76-90cd-413b-9c5b-f65b93d4bbed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c9db31945e8e767c9b1f1a9a4d16513b704e5e52
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33166959"
---
# <a name="sortheap-stlclr"></a>sort_heap (STL/CLR)
Konwertuje stertę na sortowany zakres.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<class _RanIt> inline  
    void sort_heap(_RanIt _First, _RanIt _Last);  
template<class _RanIt, class _Pr> inline  
    void sort_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `sort_heap`. Aby uzyskać więcej informacji, zobacz [sort_heap —](../standard-library/algorithm-functions.md#sort_heap).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/algorytm >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)