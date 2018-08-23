---
title: Runtimeclassflags — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassFlags
dev_langs:
- C++
helpviewer_keywords:
- RuntimeClassFlags structure
ms.assetid: 7098d605-bd14-4d51-82f4-3def8296a938
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f0a32fc373900af1a4322f4f2511c44417d2916a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594277"
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
|[RuntimeClassFlags::value, stała](../windows/runtimeclassflags-value-constant.md)|Zawiera [runtimeclasstype — wyliczenie](../windows/runtimeclasstype-enumeration.md) wartość.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`RuntimeClassFlags`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)