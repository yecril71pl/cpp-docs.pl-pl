---
title: ComPtr::Swap — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::Swap
dev_langs:
- C++
helpviewer_keywords:
- Swap method
ms.assetid: 74275f00-b24e-4b4c-b8b6-ac2aa2dd7ae9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 45bc87ec63088fe8f44411a8e86438ebab706e3f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33883488"
---
# <a name="comptrswap-method"></a>ComPtr::Swap — Metoda
Zamienia interfejsu zarządzanych przez bieżący comptr — przy użyciu interfejsu zarządzana przez określony comptr —.  
  
## <a name="syntax"></a>Składnia  
  
```  
void Swap(  
   _Inout_ ComPtr&& r  
);  
  
void Swap(  
   _Inout_ ComPtr& r  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `r`  
 Comptr —.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [ComPtr, klasa](../windows/comptr-class.md)