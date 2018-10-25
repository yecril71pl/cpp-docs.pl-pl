---
title: zapis (atrybut C++ COM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.entry
dev_langs:
- C++
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ae14a6346f547d8c362bad478144e915ee9ebb98
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077299"
---
# <a name="entry"></a>entry

Określa eksportowanych funkcji lub stałą w module, określając punkt wejścia w DLL.

## <a name="syntax"></a>Składnia

```cpp
[ entry(id) ]
```

### <a name="parameters"></a>Parametry

*id*<br/>
Identyfikator punktu wejścia.

## <a name="remarks"></a>Uwagi

**Wpis** atrybut C++ ma taką samą funkcjonalność jak [wpis](/windows/desktop/Midl/entry) atrybutów w MIDL.

## <a name="example"></a>Przykład

Zobacz przykład [idl_module](idl-module.md) dla przykładowe **wpis**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|`idl_module` Atrybut|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)