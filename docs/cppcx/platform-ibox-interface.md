---
title: Platform::IBox, interfejs
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Namespace not found::Platform
- VCCORLIB/Namespace not found::Platform::Value
ms.assetid: 774df45d-f8a7-45a3-ae24-eecc3c681040
ms.openlocfilehash: 24e70ad646e2673869b135e8cc7657910b9b499c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383298"
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

`IBox<T>` Interfejsu jest głównie używana wewnętrznie do reprezentowania typy o wartości zerowalnej zgodnie z opisem w [klasy i struktury wartości (C++/CX)](../cppcx/value-classes-and-structs-c-cx.md). Interfejs umożliwia również typy wartości pola, które są przekazywane do metod języka C++, które przyjmują parametry typu `Object^`. Można jawnie deklarować jako parametr wejściowy `IBox<SomeValueType>`. Aby uzyskać przykład, zobacz [pakowania](../cppcx/boxing-c-cx.md).

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

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)
