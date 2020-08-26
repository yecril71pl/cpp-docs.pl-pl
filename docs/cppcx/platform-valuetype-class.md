---
title: 'Platform:: ValueType, Klasa'
ms.date: 02/03/2017
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ValueType::ToString
helpviewer_keywords:
- Platform::ValueType Class
ms.assetid: 79aa8754-b140-4974-a5b1-be046938a10a
ms.openlocfilehash: f4ce34fa3f197424833d34bdb866712d412e69c3
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846553"
---
# <a name="platformvaluetype-class"></a>Platform:: ValueType, Klasa

Klasa bazowa dla wystąpień typów wartości.

## <a name="syntax"></a>Składnia

```cpp
public ref class ValueType : Object
```

## <a name="public-methods"></a>Metody publiczne

| Nazwa | Opis |
|--|--|
| [ValueType:: ToString](#tostring) | Zwraca reprezentację obiektu w postaci ciągu. Dziedziczone z [obiektu platform:: Object](../cppcx/platform-object-class.md). |

### <a name="remarks"></a>Uwagi

Klasa ValueType służy do konstruowania typów wartości. Element ValueType jest wyprowadzany z obiektu, który ma podstawowe składowe. Jednak kompilator odłącza te elementy podstawowe od typów wartości, które są wyprowadzane z klasy ValueType. Kompilator dołącza te podstawowe elementy członkowskie, gdy typ wartości jest opakowany.

### <a name="requirements"></a>Wymagania

**Minimalny obsługiwany klient:** System Windows 8

**Minimalny obsługiwany serwer:** System Windows Server 2012

**Przestrzeń nazw:** Platformach

**Metadane:** obiekt platform. winmd

## <a name="valuetypetostring-method"></a><a name="tostring"></a> ValueType:: ToString — Metoda

Zwraca reprezentację obiektu w postaci ciągu.

### <a name="syntax"></a>Składnia

```cpp
Platform::String ToString();
```

### <a name="return-value"></a>Wartość zwracana

Platform:: String, która reprezentuje wartość.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)
