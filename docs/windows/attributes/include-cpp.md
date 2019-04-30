---
title: Uwzględnij (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.include
helpviewer_keywords:
- include attribute
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
ms.openlocfilehash: d9c68601bea4cecd92b371dada5fb086aeb7657f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409450"
---
# <a name="include-c"></a>include (C++)

Określa jeden lub więcej plików nagłówka do uwzględnienia w pliku .idl wygenerowany.

## <a name="syntax"></a>Składnia

```cpp
[ include(header_file) ];
```

### <a name="parameters"></a>Parametry

*header_file*<br/>
Nazwa pliku, którego chcesz zawarte w pliku .idl wygenerowany.

## <a name="remarks"></a>Uwagi

**Obejmują** atrybut C++ powoduje `#include` instrukcję, aby umieszczona pod `import "docobj.idl"` instrukcja w pliku .idl wygenerowany.

**Obejmują** atrybut C++ ma taką samą funkcjonalność jak [obejmują](/windows/desktop/Midl/include) atrybutów w MIDL.

## <a name="example"></a>Przykład

Poniższy kod przedstawia przykład sposobu użycia **obejmują**. W tym przykładzie include.h plik zawiera tylko `#include` instrukcji.

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
|**Dotyczy**|Dowolne miejsce|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Oddzielne atrybuty](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[includelib](includelib-cpp.md)<br/>
[importlib](importlib.md)