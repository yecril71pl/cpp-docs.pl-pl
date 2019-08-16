---
title: include (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.include
helpviewer_keywords:
- include attribute
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
ms.openlocfilehash: ece88ebd7b5d9d81beb871427b58a72b2cf02022
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514548"
---
# <a name="include-c"></a>include (C++)

Określa co najmniej jeden plik nagłówka do uwzględnienia w wygenerowanym pliku IDL.

## <a name="syntax"></a>Składnia

```cpp
[ include(header_file) ];
```

### <a name="parameters"></a>Parametry

*header_file*<br/>
Nazwa pliku, który ma zostać uwzględniony w wygenerowanym pliku IDL.

## <a name="remarks"></a>Uwagi

Atrybut **include** C++ powoduje umieszczenie `import "docobj.idl"` instrukcji poniżej instrukcji w wygenerowanym pliku IDL. `#include`

Atrybut **include** C++ ma takie same funkcje jak atrybut [include](/windows/win32/Midl/include) MIDL.

## <a name="example"></a>Przykład

Poniższy kod przedstawia przykład użycia metody **include**. W tym przykładzie plik zawiera. h zawiera tylko `#include` instrukcję.

```cpp
// cpp_attr_ref_include.cpp
// compile with: /LD
[module(name="MyLib")];
[include(cpp_attr_ref_include.h)];
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

[Atrybuty IDL](idl-attributes.md)<br/>
[Oddzielne atrybuty](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[includelib](includelib-cpp.md)<br/>
[importlib](importlib.md)