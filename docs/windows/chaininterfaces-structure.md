---
title: Chaininterfaces — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces
dev_langs:
- C++
helpviewer_keywords:
- ChainInterfaces structure
ms.assetid: d7415b59-5468-4bef-a3fd-8d82b12f0e9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 88ddd3dd59000b629f6e72933b1a0b02cc582c89
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409874"
---
# <a name="chaininterfaces-structure"></a>ChainInterfaces — Struktura

Określa funkcje weryfikacji i inicjowania, które może odnosić się do zestawu interfejsu identyfikatorów.

## <a name="syntax"></a>Składnia

```cpp
template <
   typename I0,
   typename I1,
   typename I2 = Details::Nil,
   typename I3 = Details::Nil,
   typename I4 = Details::Nil,
   typename I5 = Details::Nil,
   typename I6 = Details::Nil,
   typename I7 = Details::Nil,
   typename I8 = Details::Nil,
   typename I9 = Details::Nil
>
struct ChainInterfaces : I0;
template <
   typename DerivedType,
   typename BaseType,
   bool hasImplements,
   typename I1,
   typename I2,
   typename I3,
   typename I4,
   typename I5,
   typename I6,
   typename I7,
   typename I8,
   typename I9
>
struct ChainInterfaces<MixIn<DerivedType, BaseType, hasImplements>, I1, I2, I3, I4, I5, I6, I7, I8, I9>;
```

### <a name="parameters"></a>Parametry

*I0*<br/>
(Wymagane) Identyfikator interfejsu: 0.

*I1*<br/>
(Wymagane) Identyfikator interfejsu: 1.

*I2*<br/>
(Opcjonalnie) Identyfikator interfejsu: 2.

*I3*<br/>
(Opcjonalnie) Identyfikator interfejsu 3.

*I4*<br/>
(Opcjonalnie) Identyfikator interfejsu: 4.

*I5*<br/>
(Opcjonalnie) Identyfikator interfejsu 5.

*I6*<br/>
(Opcjonalnie) Identyfikator interfejsu 6.

*I7*<br/>
(Opcjonalnie) Identyfikator interfejsu 7.

*I8*<br/>
(Opcjonalnie) Identyfikator interfejsu 8.

*I9*<br/>
(Opcjonalnie) Identyfikator interfejsu: 9.

*DerivedType*<br/>
Typ pochodny.

*BaseType*<br/>
Typ podstawowy typu pochodnego.

*hasImplements*<br/>
Wartość logiczna, że jeśli **true**, oznacza, że nie można użyć [domieszki](../windows/mixin-structure.md) struktury z klasą, która nie pochodzi od [implementuje](../windows/implements-structure.md) stucture.

## <a name="members"></a>Elementy członkowskie

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[ChainInterfaces::CanCastTo, metoda](../windows/chaininterfaces-cancastto-method.md)|Wskazuje, czy identyfikator określonego interfejsu, mogą być rzutowane na każdej specjalizacji definicją **ChainInterface** parametry szablonu.|
|[ChainInterfaces::CastToUnknown, metoda](../windows/chaininterfaces-casttounknown-method.md)|Rzutuje wskaźnika interfejsu typu zdefiniowanego przez *I0* parametr szablonu na wskaźnik do `IUnknown`.|
|[ChainInterfaces::FillArrayWithIid, metoda](../windows/chaininterfaces-fillarraywithiid-method.md)|Identyfikator interfejsu zdefiniowanych przez magazynów *I0* parametru szablonu w określonej lokalizacji w określonej tablicy interfejsu identyfikatorów.|
|[ChainInterfaces::Verify, metoda](../windows/chaininterfaces-verify-method.md)|Sprawdza, czy każdy interfejs zdefiniowany przez parametry szablonu *I0* za pośrednictwem *I9* dziedziczy `IUnknown` i/lub `IInspectable`oraz że *I0* dziedziczy z *I1* za pośrednictwem *I9*.|

### <a name="protected-constants"></a>Stałe chronione

|Nazwa|Opis|
|----------|-----------------|
|[ChainInterfaces::IidCount, stała](../windows/chaininterfaces-iidcount-constant.md)|Całkowita liczba interfejsu identyfikatory zawarte w interfejsach, określonego przez parametry szablonu *I0* za pośrednictwem *I9*.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`I0`

`ChainInterfaces`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)