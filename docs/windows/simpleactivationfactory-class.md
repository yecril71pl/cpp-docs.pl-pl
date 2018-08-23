---
title: Simpleactivationfactory — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- SimpleActivationFactory class
ms.assetid: aff768e0-0038-4fd7-95d2-ad7d308da41c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0820012c8c22de1287fcb09037212b870a4ff7bf
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594801"
---
# <a name="simpleactivationfactory-class"></a>SimpleActivationFactory — Klasa

Udostępnia mechanizm podstawowych do utworzenia środowiska uruchomieniowego Windows lub klasycznego modelu COM klasy bazowej.

## <a name="syntax"></a>Składnia

```cpp
template<typename Base>
class SimpleActivationFactory : public ActivationFactory<>;
```

### <a name="parameters"></a>Parametry

*podstawowy*  
Klasa bazowa.

## <a name="remarks"></a>Uwagi

Klasa bazowa musi dostarczać domyślnego konstruktora.

Poniższy przykład kodu demonstruje sposób używania simpleactivationfactory — za pomocą [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md) makra.

`ActivatableClassWithFactoryEx(MyClass, SimpleActivationFactory, MyServerName);`

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[SimpleActivationFactory::ActivateInstance, metoda](../windows/simpleactivationfactory-activateinstance-method.md)|Tworzy wystąpienie określonego interfejsu.|
|[SimpleActivationFactory::GetRuntimeClassName, metoda](../windows/simpleactivationfactory-getruntimeclassname-method.md)|Pobiera nazwę klasy środowiska uruchomieniowego wystąpienia klasy określonej przez *Base* parametru szablonu klasy.|
|[SimpleActivationFactory::GetTrustLevel, metoda](../windows/simpleactivationfactory-gettrustlevel-method.md)|Pobiera poziom zaufania wystąpienia klasy określonej przez *Base* parametru szablonu klasy.|

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

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)