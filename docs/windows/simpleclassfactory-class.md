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
ms.openlocfilehash: debb78ba4be2731b8cffce1133518b0b4a04f63d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="simpleclassfactory-class"></a>SimpleClassFactory — Klasa
Udostępnia mechanizm podstawowych, aby utworzyć klasę podstawową.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename Base>  
class SimpleClassFactory : public ClassFactory<>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `Base`  
 Klasa podstawowa.  
  
## <a name="remarks"></a>Uwagi  
 Klasa podstawowa musi dostarczyć konstruktora domyślnego.  
  
 Poniższy przykład kodu pokazuje sposób użycia simpleclassfactory — z [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md) makra.  
  
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
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)