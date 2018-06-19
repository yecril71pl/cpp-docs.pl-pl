---
title: HStringReference::Operator = — Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator=
dev_langs:
- C++
ms.assetid: ea100ed3-e566-4c9e-b6a8-f296088dea9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 73ec71526d340aafb16ddf2af274dce7ad0e9cbd
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875542"
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