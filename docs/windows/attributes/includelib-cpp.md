---
title: includelib — (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.includelib
helpviewer_keywords:
- includelib attribute
ms.assetid: cd90ea6e-5ae8-4f11-b8d1-662db95412b2
ms.openlocfilehash: 57f039eeae527dd03884b12e7d9eb424d87f597f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59030003"
---
# <a name="includelib-c"></a>includelib (C++)

Powoduje, że pliku .idl lub .h, mają zostać uwzględnione w pliku .idl wygenerowany.

## <a name="syntax"></a>Składnia

```cpp
[ includelib(name.idl) ];
```

### <a name="parameters"></a>Parametry

*name.idl*<br/>
Nazwa pliku .idl, którego mają być dołączane jako część pliku .idl wygenerowany.

## <a name="remarks"></a>Uwagi

**Includelib —** atrybut C++ powoduje pliku .idl lub .h, mają zostać uwzględnione w pliku .idl wygenerowany po `importlib` instrukcji.

## <a name="example"></a>Przykład

Poniższy kod jest pokazywana w pliku .cpp:

```cpp
// cpp_attr_ref_includelib.cpp
// compile with: /LD
[module(name="MyLib")];
[includelib("includelib.idl")];
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Dowolne miejsce|
|**Powtarzalne**|Tak|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Oddzielne atrybuty](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[include](include-cpp.md)<br/>
[importlib](importlib.md)