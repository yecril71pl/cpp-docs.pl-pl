---
title: Platform::ValueType, klasa
ms.date: 02/03/2017
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ValueType::ToString
helpviewer_keywords:
- Platform::ValueType Class
ms.assetid: 79aa8754-b140-4974-a5b1-be046938a10a
ms.openlocfilehash: 889cf3a53468491517d37978ca09472756ad9b7e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182954"
---
# <a name="platformvaluetype-class"></a>Platform::ValueType, klasa

Klasa bazowa dla wystąpień typów wartości.

## <a name="syntax"></a>Składnia

```cpp
public ref class ValueType : Object
```

## <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|[ValueType::ToString](#tostring)|Zwraca reprezentację ciągu obiektu. Odziedziczone po [Platform::Object](../cppcx/platform-object-class.md).|

### <a name="remarks"></a>Uwagi

Klasa ValueType jest używana do tworzenia typów wartości. Element ValueType pochodzi z obiektu, który zawiera podstawowe składniki. Jednak kompilator odłącza tych podstawowych członków z typów wartości, które pochodzą z klasy ValueType. Kompilator ponowne dołączenie następuje ponowne tych podstawowych elementów członkowskich, gdy typ wartości jest spakowany.

### <a name="requirements"></a>Wymagania

**Minimalna obsługiwana klienta:** Windows 8

**Minimalna obsługiwana serwera:** Windows Server 2012

**Namespace:** Platforma

**Metadane:** platform.winmd

## <a name="tostring"></a> Metoda ValueType::ToString

Zwraca reprezentację ciągu obiektu.

### <a name="syntax"></a>Składnia

```cpp
Platform::String ToString();
```

### <a name="return-value"></a>Wartość zwracana

Platform::String, który reprezentuje wartość.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)
