---
title: Simpleclassfactory — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleClassFactory
dev_langs:
- C++
helpviewer_keywords:
- SimpleClassFactory class
ms.assetid: 6edda1b2-4e44-4e14-9364-72f519249962
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 21b52876cb2a6c7bbf110a06cdfb29abdf1930d6
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641832"
---
# <a name="simpleclassfactory-class"></a>SimpleClassFactory — Klasa
Zapewnia mechanizm podstawowych, aby utworzyć klasę bazową.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename Base>  
class SimpleClassFactory : public ClassFactory<>;  
```  
  
### <a name="parameters"></a>Parametry  
 *podstawowy*  
 Klasa bazowa.  
  
## <a name="remarks"></a>Uwagi  
 Klasa bazowa musi dostarczać domyślnego konstruktora.  
  
 Poniższy przykład kodu demonstruje sposób używania **simpleclassfactory —** z [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md) makra.  
  
 `ActivatableClassWithFactoryEx(MyClass, SimpleClassFactory, MyServerName);`  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[SimpleClassFactory::CreateInstance, metoda](../windows/simpleclassfactory-createinstance-method.md)|Tworzy wystąpienie określonego interfejsu.|  
  
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
  
 `ClassFactory`  
  
 `SimpleClassFactory`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)