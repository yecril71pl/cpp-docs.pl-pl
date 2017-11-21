---
title: "ClassFactory — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::ClassFactory
dev_langs: C++
helpviewer_keywords: ClassFactory class
ms.assetid: f13e6bce-722b-4f18-b7cf-3ffa6345c1db
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2c1dfeafab3ffa3c9a25c5c2284f6ca2c047a6c2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="classfactory-class"></a>ClassFactory — Klasa
Implementuje podstawowych funkcji interfejsu IClassFactory.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `I0`  
 Interfejs zeroth.  
  
 `I1`  
 Pierwszy interfejs.  
  
 `I2`  
 Drugi interfejs.  
  
## <a name="remarks"></a>Uwagi  
 Korzystanie z `ClassFactory` do implementacji fabryki zdefiniowane przez użytkownika.  
  
 Następujący wzór programowania przedstawiono sposób użycia [implementuje](../windows/implements-structure.md) struktury, aby określić więcej niż trzy interfejsy na fabrykę klas.  
  
 `struct MyFactory : ClassFactory<Implements<I1, I2, I3>, I4, I5>`  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ClassFactory::ClassFactory — Konstruktor](../windows/classfactory-classfactory-constructor.md)||  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ClassFactory::AddRef — metoda](../windows/classfactory-addref-method.md)|Zwiększa liczbę odwołania dla bieżącego obiektu ClassFactory —.|  
|[ClassFactory::LockServer — metoda](../windows/classfactory-lockserver-method.md)|Zwiększa lub zmniejsza liczbę podstawowych obiektów, które są śledzone przez bieżący obiekt ClassFactory —.|  
|[ClassFactory::QueryInterface — metoda](../windows/classfactory-queryinterface-method.md)|Pobiera wskaźnik do interfejsu określonego przez parametr.|  
|[ClassFactory::Release — metoda](../windows/classfactory-release-method.md)|Liczba odwołania dla bieżącego obiektu ClassFactory — zmniejsza.|  
  
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
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl — Namespace](../windows/microsoft-wrl-namespace.md)   
 [Runtimeclasstype — wyliczenie](../windows/runtimeclasstype-enumeration.md)