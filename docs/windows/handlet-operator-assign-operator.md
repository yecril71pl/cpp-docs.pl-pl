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
ms.openlocfilehash: ab629946b9fc5acec6b0fb0ba8f573a3fa90a031
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570044"
---
# <a name="handletoperator-operator"></a>HandleT::operator= Operator
Przenosi wartość określonego **HandleT** obiekt do bieżącego **HandleT** obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HandleT& operator=(  
   _Inout_ HandleT&& h  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *h*  
 Odwołanie rvalue do uchwytu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Odwołanie do bieżącego **HandleT** obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Ta operacja powoduje unieważnienie **HandleT** obiekt określony przez parametr *h*.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers  
  
## <a name="see-also"></a>Zobacz też  
 [HandleT, klasa](../windows/handlet-class.md)