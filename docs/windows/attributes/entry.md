---
title: entry (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.entry
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
ms.openlocfilehash: 63e5ccebb1d3844af8dd11b4b094abe96e3e257c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845318"
---
# <a name="entry"></a>entry

Określa wyeksportowaną funkcję lub stałą w module, identyfikując punkt wejścia w bibliotece DLL.

## <a name="syntax"></a>Składnia

```cpp
[ entry(id) ]
```

### <a name="parameters"></a>Parametry

*id*<br/>
Identyfikator punktu wejścia.

## <a name="remarks"></a>Uwagi

**Wpis** C++ Attribute ma takie same funkcje jak atrybut MIDL [wpisu](/windows/win32/Midl/entry) .

## <a name="example"></a>Przykład

Zapoznaj się z przykładem [idl_module](idl-module.md) , aby zapoznać się z przykładem zastosowania **wpisów**.

## <a name="requirements"></a>Wymagania

| Kontekst atrybutu | Wartość |
|-|-|
|**Dotyczy**|Atrybut `idl_module`|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)
