---
title: Runtimeclassflags — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/07/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassFlags
- implements/Microsoft::WRL::RuntimeClassFlags::value
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::RuntimeClassFlags structure
- Microsoft::WRL::RuntimeClassFlags::value constant
ms.assetid: 7098d605-bd14-4d51-82f4-3def8296a938
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6c3cb141576598aa39c718316048900622c4df41
ms.sourcegitcommit: fb9448eb96c6351a77df04af16ec5c0fb9457d9e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44691461"
---
# <a name="runtimeclassflags-structure"></a>RuntimeClassFlags — Struktura

Zawiera typ wystąpienia [RuntimeClass](../windows/runtimeclass-class.md).

## <a name="syntax"></a>Składnia

```cpp
template <
   unsigned int flags
>
struct RuntimeClassFlags;
```

### <a name="parameters"></a>Parametry

*flagi*  
A [runtimeclasstype — wyliczenie](../windows/runtimeclasstype-enumeration.md) wartość.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constants"></a>Publiczne stałe

|Nazwa|Opis|
|----------|-----------------|
|[RuntimeClassFlags::value, stała](#value-constant)|Zawiera [runtimeclasstype — wyliczenie](../windows/runtimeclasstype-enumeration.md) wartość.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`RuntimeClassFlags`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::WRL

## <a name="value-constant"></a>RuntimeClassFlags::value — stała

Pola, które zawiera [runtimeclasstype — wyliczenie](../windows/runtimeclasstype-enumeration.md) wartość.
  
```cpp
static const unsigned int value = flags;
```
