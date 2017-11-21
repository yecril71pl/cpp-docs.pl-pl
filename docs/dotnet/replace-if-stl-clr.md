---
title: replace_if (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::replace_if
dev_langs: C++
helpviewer_keywords: replace_if function [STL/CLR]
ms.assetid: 485ed698-551f-4808-8562-9e32b151786d
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 87e02b927e01ad1b5180c7b25b5192d370d4b009
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="replaceif-stlclr"></a>replace_if (STL/CLR)
Sprawdza każdy element w zakresie i zastępuje go, jeśli spełnia określony predykat.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<class _FwdIt, class _Pr, class _Ty> inline  
    void replace_if(_FwdIt _First, _FwdIt _Last, _Pr _Pred,  
        const _Ty% _Val);  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `replace_if`. Aby uzyskać więcej informacji, zobacz [replace_if](../standard-library/algorithm-functions.md#replace_if).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/algorytm >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [Algorytm (STL/CLR)](../dotnet/algorithm-stl-clr.md)