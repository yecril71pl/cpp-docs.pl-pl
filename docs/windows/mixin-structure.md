---
title: Mixin — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::MixIn
dev_langs:
- C++
helpviewer_keywords:
- MixIn structure
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b20dac5f189a51a1610da45e43e03e51ff1c3610
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
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
 `true` Jeśli `MixInType` jest pochodną bieżąca implementacja typu podstawowego; `false` inaczej.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli klasą pochodną zarówno interfejsy klasy COM, jak i środowiska wykonawczego systemu Windows, lista deklaracji klasy najpierw musi zawierać żadnego z interfejsów środowiska wykonawczego systemu Windows, a następnie interfejsy żadnych klasycznego modelu COM. Domieszki gwarantuje, że interfejsy są określone w poprawnej kolejności.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `MixIn`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)