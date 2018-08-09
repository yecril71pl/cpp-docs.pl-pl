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
ms.openlocfilehash: 8fb5fa5288829ef51bf818ad8b7cf3b46edb59bf
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014289"
---
# <a name="mixin-structure"></a>MixIn — Struktura
Zapewnia, że klasy środowiska uruchomieniowego pochodzi od klasy interfejsów Windows Runtime, jeśli istnieje, a następnie klasycznych interfejsów COM.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
template<  
   typename Derived,  
   typename MixInType,  
   bool hasImplements = __is_base_of(Details::ImplementsBase,  
   MixInType)  
>  
struct MixIn;  
```  
  
### <a name="parameters"></a>Parametry  
 *Pochodne*  
 Typ pochodzący od [implementuje](../windows/implements-structure.md) struktury.  
  
 *MixInType*  
 Typ podstawowy.  
  
 *hasImplements*  
 **wartość true,** Jeśli *MixInType* jest pochodną bieżąca implementacja parametru typu podstawowego; **false** inaczej.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli klasa jest pochodną klasy COM, interfejsów i środowiska wykonawczego Windows, lista deklaracji klasy, najpierw musi zawierać żadnych interfejsów Windows Runtime, a następnie wszelkie Klasyczny model COM, interfejsów. **MixIn** gwarantuje, że interfejsy są określone w poprawnej kolejności.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `MixIn`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)