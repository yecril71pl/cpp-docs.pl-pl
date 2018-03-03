---
title: "HStringReference::Operator = — Operator | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator=
dev_langs:
- C++
ms.assetid: ea100ed3-e566-4c9e-b6a8-f296088dea9c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 097e89ab4ae2d3b6ddaacb2fa52b811c1577ef72
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="hstringreferenceoperator-operator"></a>HStringReference::Operator= Operator
Przenosi bieżący obiekt hstringreference — wartość innego obiektu hstringreference —.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HStringReference& operator=(HStringReference&& other) throw()  
```  
  
#### <a name="parameters"></a>Parametry  
 `other`  
 Hstringreference — obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Wartość istniejącej `other` obiektu jest kopiowany do bieżącego obiektu hstringreference —, a następnie `other` obiekt zostanie zniszczony.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [HStringReference, klasa](../windows/hstringreference-class.md)