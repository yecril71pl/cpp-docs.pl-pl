---
title: "Simpleactivationfactory — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::SimpleActivationFactory
dev_langs: C++
helpviewer_keywords: SimpleActivationFactory class
ms.assetid: aff768e0-0038-4fd7-95d2-ad7d308da41c
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3c56d03b74080ae65f84ffbad8c4dd2092be1082
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="simpleactivationfactory-class"></a>SimpleActivationFactory — Klasa
Udostępnia mechanizm podstawowych do utworzenia środowiska wykonawczego systemu Windows lub klasycznego modelu COM klasy podstawowej.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<  
   typename Base  
>  
class SimpleActivationFactory : public ActivationFactory<>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `Base`  
 Klasa podstawowa.  
  
## <a name="remarks"></a>Uwagi  
 Klasa podstawowa musi dostarczyć konstruktora domyślnego.  
  
 Poniższy przykład kodu pokazuje sposób użycia simpleactivationfactory — z [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md) makra.  
  
 `ActivatableClassWithFactoryEx(MyClass, SimpleActivationFactory, MyServerName);`  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[SimpleActivationFactory::ActivateInstance — metoda](../windows/simpleactivationfactory-activateinstance-method.md)|Tworzy wystąpienie określonego interfejsu.|  
|[SimpleActivationFactory::GetRuntimeClassName — metoda](../windows/simpleactivationfactory-getruntimeclassname-method.md)|Pobiera nazwę klasy środowiska uruchomieniowego wystąpienia z klasą określoną przez `Base` parametr szablonu klasy.|  
|[SimpleActivationFactory::GetTrustLevel — metoda](../windows/simpleactivationfactory-gettrustlevel-method.md)|Pobiera poziom zaufania wystąpienia z klasą określoną przez `Base` parametr szablonu klasy.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `I0`  
  
 `ChainInterfaces`  
  
 `I0`  
  
 `RuntimeClassBase`  
  
 `ImplementsHelper`  
  
 `DontUseNewUseMake`  
  
 `RuntimeClassFlags`  
  
 `RuntimeClassBaseT`  
  
 `RuntimeClass`  
  
 `ActivationFactory`  
  
 `SimpleActivationFactory`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl — Namespace](../windows/microsoft-wrl-namespace.md)