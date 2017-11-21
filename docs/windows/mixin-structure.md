---
title: "Mixin — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::MixIn
dev_langs: C++
helpviewer_keywords: MixIn structure
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e1df2de0a8c645b957a5c3e93f8c4ebbb3b2fb94
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="mixin-structure"></a>MixIn — Struktura
Zapewnia, że klasa środowiska uruchomieniowego pochodzi z interfejsów środowiska wykonawczego systemu Windows, jeśli istnieje, a następnie klasycznego interfejsy modelu COM.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<  
   typename Derived,  
   typename MixInType,  
   bool hasImplements = __is_base_of(Details::ImplementsBase,  
   MixInType)  
>  
struct MixIn;  
```  
  
#### <a name="parameters"></a>Parametry  
 `Derived`  
 Typ pochodny [implementuje](../windows/implements-structure.md) struktury.  
  
 `MixInType`  
 Typ podstawowy.  
  
 `hasImplements`  
 `true`Jeśli `MixInType` jest pochodną bieżąca implementacja typu podstawowego; `false` inaczej.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli klasą pochodną zarówno interfejsy klasy COM, jak i środowiska wykonawczego systemu Windows, lista deklaracji klasy najpierw musi zawierać żadnego z interfejsów środowiska wykonawczego systemu Windows, a następnie interfejsy żadnych klasycznego modelu COM. Domieszki gwarantuje, że interfejsy są określone w poprawnej kolejności.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `MixIn`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl — Namespace](../windows/microsoft-wrl-namespace.md)