---
title: Platform::IBox, interfejs | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Namespace not found::Platform
- VCCORLIB/Namespace not found::Platform::Value
dev_langs:
- C++
ms.assetid: 774df45d-f8a7-45a3-ae24-eecc3c681040
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 540b759153b8fac0532a8817d89e704d55fbffd3
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44102081"
---
# <a name="platformibox-interface"></a>Platform::IBox, interfejs

[Platform::IBox](../cppcx/platform-ibox-interface.md) interfejs jest nazwa języka C++ dla `Windows::Foundation::IReference` interfejsu.

## <a name="syntax"></a>Składnia

```cpp
template <typename T>
interface class IBox
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ wartości spakowanej.

### <a name="remarks"></a>Uwagi

`IBox<T>` Interfejsu jest głównie używana wewnętrznie do reprezentowania typy o wartości zerowalnej zgodnie z opisem w [klasy i struktury wartości (C + +/ CX)](../cppcx/value-classes-and-structs-c-cx.md). Interfejs umożliwia również typy wartości pola, które są przekazywane do metod języka C++, które przyjmują parametry typu `Object^`. Można jawnie deklarować jako parametr wejściowy `IBox<SomeValueType>`. Aby uzyskać przykład, zobacz [pakowania](../cppcx/boxing-c-cx.md).

### <a name="requirements"></a>Wymagania

### <a name="members"></a>Elementy członkowskie

`Platform::IBox` Interfejs dziedziczy z [Platform::IValueType](../cppcx/platform-ivaluetype-interface.md) interfejsu. `IBox` ma te elementy członkowskie:

**Właściwości**

|Metoda|Opis|
|------------|-----------------|
|[Wartość](#value)|Zwraca wartość rozpakowany, które wcześniej były przechowywane w tym `IBox` wystąpienia.|

## <a name="value"></a> Właściwość IBox::Value

Zwraca wartość, która pierwotnie została zapisana w tym obiekcie.

### <a name="syntax"></a>Składnia

```cpp
property T Value {T get();}
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ wartości spakowanej.

### <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość

Zwraca wartość, która pierwotnie została zapisana w tym obiekcie.

### <a name="remarks"></a>Uwagi

Aby uzyskać przykład, zobacz [pakowania](../cppcx/boxing-c-cx.md).

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)