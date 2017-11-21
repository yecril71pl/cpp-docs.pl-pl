---
title: "Activationfactory — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::ActivationFactory
dev_langs: C++
helpviewer_keywords: ActivationFactory class
ms.assetid: 5faddf1f-43b6-4f8a-97de-8c9d3ae1e1ff
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6876fb3d418a4dac8a68449da5d0eae855daa440
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="activationfactory-class"></a>ActivationFactory — Klasa
Umożliwia co najmniej jedną klasę do aktywacji przez środowisko wykonawcze systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <  
   typename I0 = Details::Nil,  
   typename I1 = Details::Nil,  
   typename I2 = Details::Nil  
>  
class ActivationFactory : public Details::RuntimeClass<typename Details::InterfaceListHelper<IActivationFactory, I0, I1, I2, Details::Nil>::TypeT, RuntimeClassFlags<WinRt | InhibitWeakReference>, false>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `I0`  
 Interfejs zeroth.  
  
 `I1`  
 Pierwszy interfejs.  
  
 `I2`  
 Drugi interfejs.  
  
## <a name="remarks"></a>Uwagi  
 Activationfactory — udostępnia metody rejestracji i podstawowych funkcji interfejsu IActivationFactory. Activationfactory — umożliwia także fabrycznej implementacji.  
  
 Poniższy fragment kodu symbolicznie ilustruje sposób używania activationfactory —.  
  
 [!code-cpp[wrl-microsoft__wrl__activationfactory#1](../windows/codesnippet/CPP/activationfactory-class_1.cpp)]  
  
 Poniższy fragment kodu przedstawia sposób użycia [implementuje](../windows/implements-structure.md) struktury, aby określić więcej niż trzy interfejsu identyfikatorów.  
  
 `struct MyFactory : ActivationFactory<Implements<I1, I2, I3>, I4, I5>;`  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Activationfactory::activationfactory — Konstruktor](../windows/activationfactory-activationfactory-constructor.md)|Inicjuje activationfactory — klasa.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ActivationFactory::AddRef — metoda](../windows/activationfactory-addref-method.md)|Zwiększa liczbę odwołanie do bieżącego obiektu activationfactory —.|  
|[ActivationFactory::GetIids — metoda](../windows/activationfactory-getiids-method.md)|Pobiera tablica zaimplementowanego interfejsu identyfikatorów.|  
|[ActivationFactory::GetRuntimeClassName — metoda](../windows/activationfactory-getruntimeclassname-method.md)|Pobiera obiekt, który tworzy bieżącego activationfactory — Nazwa klasy środowiska wykonawczego.|  
|[ActivationFactory::GetTrustLevel — metoda](../windows/activationfactory-gettrustlevel-method.md)|Pobiera obiekt, który tworzy bieżącego activationfactory — poziom zaufania.|  
|[ActivationFactory::QueryInterface — metoda](../windows/activationfactory-queryinterface-method.md)|Pobiera wskaźnik do określonego interfejsu.|  
|[ActivationFactory::Release — metoda](../windows/activationfactory-release-method.md)|Zmniejsza odwołanie liczba bieżącego obiektu activationfactory —.|  
  
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
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl — Namespace](../windows/microsoft-wrl-namespace.md)