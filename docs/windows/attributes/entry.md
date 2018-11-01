---
title: zapis (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.entry
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
ms.openlocfilehash: b6c34a603f3ba8abaf070759a22ddf2b8e9c2106
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663258"
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