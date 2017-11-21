---
title: "HandleT::operator = — Operator | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleT::operator=
dev_langs: C++
helpviewer_keywords: operator= operator
ms.assetid: 9e42dcca-30fa-4e8b-8954-802fd64a5595
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5c71e29fa31c89c030b74843a9d776923fed6789
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Handlet — klasa](../windows/handlet-class.md)