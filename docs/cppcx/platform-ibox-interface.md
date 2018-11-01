---
title: Platform::IBox, interfejs
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Namespace not found::Platform
- VCCORLIB/Namespace not found::Platform::Value
ms.assetid: 774df45d-f8a7-45a3-ae24-eecc3c681040
ms.openlocfilehash: 4cca648b3b81dbf0d9f8d3e5f87625464f1d8385
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625050"
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