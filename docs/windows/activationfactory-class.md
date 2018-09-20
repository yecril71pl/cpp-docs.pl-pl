---
title: Activationfactory — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- ActivationFactory class
ms.assetid: 5faddf1f-43b6-4f8a-97de-8c9d3ae1e1ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 55c82290c3a96ab71419b36a7ec4a4eb2b528753
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419818"
---
# <a name="activationfactory-class"></a>ActivationFactory — Klasa

Umożliwia co najmniej jedną klasę na uaktywnianie przez środowisko wykonawcze Windows.

## <a name="syntax"></a>Składnia

```cpp
template <
   typename I0 = Details::Nil,
   typename I1 = Details::Nil,
   typename I2 = Details::Nil
>
class ActivationFactory : public Details::RuntimeClass<typename Details::InterfaceListHelper<IActivationFactory, I0, I1, I2, Details::Nil>::TypeT, RuntimeClassFlags<WinRt | InhibitWeakReference>, false>;
```

### <a name="parameters"></a>Parametry

*I0*<br/>
Interfejsu zerowego.

*I1*<br/>
Pierwszy interfejs.

*I2*<br/>
Drugi interfejs.

## <a name="remarks"></a>Uwagi

**Activationfactory —** udostępnia metody rejestracji i podstawowe funkcje dla `IActivationFactory` interfejsu. **Activationfactory —** oferuje również możliwość implementacji niestandardowych fabryki.

Poniższy fragment kodu ilustruje symbolicznie sposób użycia activationfactory —.

[!code-cpp[wrl-microsoft__wrl__activationfactory#1](../windows/codesnippet/CPP/activationfactory-class_1.cpp)]

Poniższy fragment kodu przedstawia sposób użycia [implementuje](../windows/implements-structure.md) struktury, aby określić więcej niż trzy identyfikatory interfejsu.

`struct MyFactory : ActivationFactory<Implements<I1, I2, I3>, I4, I5>;`

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[ActivationFactory::ActivationFactory, konstruktor](../windows/activationfactory-activationfactory-constructor.md)|Inicjuje **activationfactory —** klasy.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[ActivationFactory::AddRef, metoda](../windows/activationfactory-addref-method.md)|Zwiększa liczbę odwołań bieżącego **activationfactory —** obiektu.|
|[ActivationFactory::GetIids, metoda](../windows/activationfactory-getiids-method.md)|Pobiera tablicę zaimplementowanego interfejsu identyfikatorów.|
|[ActivationFactory::GetRuntimeClassName, metoda](../windows/activationfactory-getruntimeclassname-method.md)|Pobiera nazwę klasy środowiska uruchomieniowego, obiektu, który bieżącego **activationfactory —** tworzy wystąpienie.|
|[ActivationFactory::GetTrustLevel, metoda](../windows/activationfactory-gettrustlevel-method.md)|Pobiera poziom zaufania, obiektu, który bieżącego **activationfactory —** tworzy wystąpienie.|
|[ActivationFactory::QueryInterface, metoda](../windows/activationfactory-queryinterface-method.md)|Pobiera wskaźnik do określonego interfejsu.|
|[ActivationFactory::Release, metoda](../windows/activationfactory-release-method.md)|Dekrementuje liczbę odwołań bieżącego **activationfactory —** obiektu.|

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

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)