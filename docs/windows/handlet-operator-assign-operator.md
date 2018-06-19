---
title: HandleT::operator = — Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: 9e42dcca-30fa-4e8b-8954-802fd64a5595
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6a13e8eb7e74625e185b59816b5794b0390e95e3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873930"
---
# <a name="handletoperator-operator"></a>HandleT::operator= Operator
Przenosi bieżący obiekt handlet — wartość określonego obiektu handlet —.  
  
## <a name="syntax"></a>Składnia  
  
```  
HandleT& operator=(  
   _Inout_ HandleT&& h  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `h`  
 R-wartości — odwołanie do uchwytu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Odwołanie do bieżącego obiektu handlet —.  
  
## <a name="remarks"></a>Uwagi  
 Ta operacja powoduje unieważnienie obiektu handlet — określonej przez parametr `h`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [HandleT, klasa](../windows/handlet-class.md)