---
title: includelib — (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.includelib
helpviewer_keywords:
- includelib attribute
ms.assetid: cd90ea6e-5ae8-4f11-b8d1-662db95412b2
ms.openlocfilehash: 30e84a6c82ec25e07ca0eb08f64c7aa5b560e9e7
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88830699"
---
# <a name="includelib-c"></a>includelib (C++)

Powoduje, że plik IDL lub h zostanie uwzględniony w wygenerowanym pliku IDL.

## <a name="syntax"></a>Składnia

```cpp
[ includelib(name.idl) ];
```

### <a name="parameters"></a>Parametry

*Nazwa. idl*<br/>
Nazwa pliku. idl, który ma zostać uwzględniony jako część wygenerowanego pliku IDL.

## <a name="remarks"></a>Uwagi

Atrybut **includelib —** C++ powoduje, że plik IDL lub h zostanie uwzględniony w wygenerowanym pliku IDL, po `importlib` instrukcji.

## <a name="example"></a>Przykład

Poniższy kod jest przedstawiony w pliku. cpp:

```cpp
// cpp_attr_ref_includelib.cpp
// compile with: /LD
[module(name="MyLib")];
[includelib("includelib.idl")];
```

## <a name="requirements"></a>Wymagania

| Kontekst atrybutu | Wartość |
|-|-|
|**Dotyczy**|Dowolne miejsce|
|**Powtarzalne**|Tak|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty autonomiczne](stand-alone-attributes.md)<br/>
[zaimportować](import.md)<br/>
[importidl](importidl.md)<br/>
[być](include-cpp.md)<br/>
[importlib](importlib.md)
