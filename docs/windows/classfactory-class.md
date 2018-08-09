---
title: ClassFactory — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory
dev_langs:
- C++
helpviewer_keywords:
- ClassFactory class
ms.assetid: f13e6bce-722b-4f18-b7cf-3ffa6345c1db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c9a7caba7ccfb8f5764a1f460835ff540c838975
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641044"
---
# <a name="classfactory-class"></a>ClassFactory — Klasa
Implementuje podstawowe funkcje `IClassFactory` interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
template <  
   typename I0 = Details::Nil,  
   typename I1 = Details::Nil,  
   typename I2 = Details::Nil  
>  
class ClassFactory : public Details::RuntimeClass<  
   typename Details::InterfaceListHelper<IClassFactory,   
   I0,   
   I1,   
   I2,   
   Details::Nil>::TypeT,   
   RuntimeClassFlags<ClassicCom | InhibitWeakReference>,   
      false>;  
```  
  
### <a name="parameters"></a>Parametry  
 *I0*  
 Interfejsu zerowego.  
  
 *I1*  
 Pierwszy interfejs.  
  
 *I2*  
 Drugi interfejs.  
  
## <a name="remarks"></a>Uwagi  
 Korzystanie z **ClassFactory —** do implementacji fabryki zdefiniowanych przez użytkownika.  
  
 Następujący wzorzec programowania pokazuje sposób użycia [implementuje](../windows/implements-structure.md) struktury, aby określić więcej niż trzy interfejsy na fabrykę klas.  
  
 `struct MyFactory : ClassFactory<Implements<I1, I2, I3>, I4, I5>`  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ClassFactory::ClassFactory, konstruktor](../windows/classfactory-classfactory-constructor.md)||  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ClassFactory::AddRef, metoda](../windows/classfactory-addref-method.md)|Zwiększa liczbę odwołań dla bieżącego **ClassFactory —** obiektu.|  
|[ClassFactory::LockServer, metoda](../windows/classfactory-lockserver-method.md)|Zwiększa lub zmniejsza liczbę podstawowych obiektów, które są śledzone przez bieżącą **ClassFactory —** obiektu.|  
|[ClassFactory::QueryInterface, metoda](../windows/classfactory-queryinterface-method.md)|Pobiera wskaźnik do interfejsu, określony przez parametr.|  
|[ClassFactory::Release, metoda](../windows/classfactory-release-method.md)|Dekrementuje liczbę odwołań dla bieżącego **ClassFactory —** obiektu.|  
  
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
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)   
 [RuntimeClassType, wyliczenie](../windows/runtimeclasstype-enumeration.md)