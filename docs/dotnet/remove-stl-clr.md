---
title: Usuń (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::remove
dev_langs:
- C++
helpviewer_keywords:
- remove function [STL/CLR]
ms.assetid: 85a11883-3e25-49aa-b4a0-b2cffd6dc110
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e9ef7b6039a3243c52f4c2de56ef73f3afc13b80
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33162814"
---
# <a name="remove-stlclr"></a>remove (STL/CLR)
Eliminuje określoną wartość z danego zakresu bez zakłócania kolejności pozostałych elementów i zwracania końca nowego zakresu wolnego od określonej wartości.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<class _FwdIt, class _Ty> inline  
    _FwdIt remove(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `remove`. Aby uzyskać więcej informacji, zobacz [Usuń](http://msdn.microsoft.com/Library/77e2585c-441e-448d-bd1d-c893d1356ed8).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/algorytm >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)