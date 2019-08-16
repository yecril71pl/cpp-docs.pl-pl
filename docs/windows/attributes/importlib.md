---
title: importlib (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.importlib
helpviewer_keywords:
- importlib attribute
ms.assetid: f129e459-b8d3-4aca-a0bc-ee53e18b62ed
ms.openlocfilehash: 92cf335e5c4754595f2c7af2e1aef30d309d2f5f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514605"
---
# <a name="importlib"></a>importlib

Sprawia, że typy, które zostały już skompilowane w innej bibliotece typów dostępne dla tworzonej biblioteki typów.

## <a name="syntax"></a>Składnia

```cpp
[ importlib("tlb_file") ];
```

### <a name="parameters"></a>Parametry

*tlb_file*<br/>
Nazwa pliku. tlb, w cudzysłowie, która ma zostać zaimportowana do biblioteki typów w bieżącym projekcie.

## <a name="remarks"></a>Uwagi

Atrybut **importlib** C++ powoduje umieszczenie instrukcjiwblokubibliotekiwygenerowanegoplikuIDL.`importlib` Atrybut **importlib** ma takie same funkcje jak atrybut [importlib](/windows/win32/Midl/importlib) MIDL.

## <a name="example"></a>Przykład

Poniższy kod przedstawia przykład użycia **importlib**:

```cpp
// cpp_attr_ref_importlib.cpp
// compile with: /LD
[module(name="MyLib")];
[importlib("importlib.tlb")];
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Dowolnym miejscu|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty kompilatora](compiler-attributes.md)<br/>
[Oddzielne atrybuty](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)