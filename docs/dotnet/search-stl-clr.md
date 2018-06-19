---
title: Wyszukiwanie (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::search
dev_langs:
- C++
helpviewer_keywords:
- search function [STL/CLR]
ms.assetid: 3317c7f4-9f47-44b8-a7c7-73948a2f83e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e0fb0b045e15c5ab491f0f7a4f2514898526b8fc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33162749"
---
# <a name="search-stlclr"></a>search (STL/CLR)
Wyszukuje pierwsze wystąpienie sekwencji w zakresie docelowym, której elementy są równe tym w danej sekwencji elementów lub której elementy są równoważne w sensie określonym przez predykat binarny dla elementów w danej sekwencji.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<class _FwdIt1, class _FwdIt2> inline  
    _FwdIt1 search(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _FwdIt2 _First2, _FwdIt2 _Last2);  
template<class _FwdIt1, class _FwdIt2, class _Pr> inline  
    _FwdIt1 search(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `search`. Aby uzyskać więcej informacji, zobacz [wyszukiwania](../standard-library/algorithm-functions.md#search).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/algorytm >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)