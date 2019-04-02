---
title: RuntimeClassFlags — Struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassFlags
- implements/Microsoft::WRL::RuntimeClassFlags::value
helpviewer_keywords:
- Microsoft::WRL::RuntimeClassFlags structure
- Microsoft::WRL::RuntimeClassFlags::value constant
ms.assetid: 7098d605-bd14-4d51-82f4-3def8296a938
ms.openlocfilehash: 4cbd3f367bc57c2eedf672422a458b67b1908fc0
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787255"
---
# <a name="runtimeclassflags-structure"></a>RuntimeClassFlags — Struktura

Zawiera typ wystąpienia [RuntimeClass](runtimeclass-class.md).

## <a name="syntax"></a>Składnia

```cpp
template <unsigned int flags>
struct RuntimeClassFlags;
```

### <a name="parameters"></a>Parametry

*flagi*<br/>
A [runtimeclasstype — wyliczenie](runtimeclasstype-enumeration.md) wartość.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constants"></a>Publiczne stałe

|Nazwa|Opis|
|----------|-----------------|
|[RuntimeClassFlags::value, stała](#value-constant)|Zawiera [runtimeclasstype — wyliczenie](runtimeclasstype-enumeration.md) wartość.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`RuntimeClassFlags`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::WRL

## <a name="value-constant"></a>RuntimeClassFlags::value Constant

Pola, które zawiera [runtimeclasstype — wyliczenie](runtimeclasstype-enumeration.md) wartość.

```cpp
static const unsigned int value = flags;
```
