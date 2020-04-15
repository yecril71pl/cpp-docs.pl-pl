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
ms.openlocfilehash: 9fed5bb31b077288495a78aefcbd8401b3520bb6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367225"
---
# <a name="runtimeclassflags-structure"></a>RuntimeClassFlags — Struktura

Zawiera typ wystąpienia [runtimeclass](runtimeclass-class.md).

## <a name="syntax"></a>Składnia

```cpp
template <unsigned int flags>
struct RuntimeClassFlags;
```

### <a name="parameters"></a>Parametry

*flagi*<br/>
Wartość [wyliczenia typu RuntimeClassType.](runtimeclasstype-enumeration.md)

## <a name="members"></a>Elementy członkowskie

### <a name="public-constants"></a>Stałe publiczne

|Nazwa|Opis|
|----------|-----------------|
|[RuntimeClassFlags::value, stała](#value-constant)|Zawiera wartość [wyliczenia typu RuntimeClassType.](runtimeclasstype-enumeration.md)|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`RuntimeClassFlags`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Obszar nazw:** Microsoft::WRL

## <a name="runtimeclassflagsvalue-constant"></a><a name="value-constant"></a>RuntimeClassFlags::wartość stała

Pole zawierające wartość [wyliczenia runtimeClassType.](runtimeclasstype-enumeration.md)

```cpp
static const unsigned int value = flags;
```
