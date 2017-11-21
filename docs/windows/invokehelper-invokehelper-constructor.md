---
title: "Invokehelper::invokehelper — Konstruktor | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: event/Microsoft::WRL::Details::InvokeHelper::InvokeHelper
dev_langs: C++
helpviewer_keywords: InvokeHelper, constructor
ms.assetid: 0223c574-abc3-4fc0-99e6-38626ba79243
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b80953302abe5369044d59deaf6d4286a6941083
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="invokehelperinvokehelper-constructor"></a>InvokeHelper::InvokeHelper — Konstruktor
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
explicit InvokeHelper(  
   TCallback callback  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `callback`  
 Program obsługi zdarzeń.  
  
## <a name="remarks"></a>Uwagi  
 Inicjuje nowe wystąpienie klasy invokehelper —.  
  
 `TCallback` Parametr szablonu określa typ obsługi zdarzeń.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** event.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Invokehelper — struktura](../windows/invokehelper-structure.md)   
 [Microsoft::wrl:: details — Namespace](../windows/microsoft-wrl-details-namespace.md)