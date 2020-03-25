---
title: importidl (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.importidl
helpviewer_keywords:
- importidl attribute
ms.assetid: 4b0a4b55-6c57-4e6e-bc7b-a12cc8063941
ms.openlocfilehash: 6e41a98bef079c92b6df6e7eff203301aa9ceae4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166825"
---
# <a name="importidl"></a>importidl

Wstawia określony plik IDL do wygenerowanego pliku IDL.

## <a name="syntax"></a>Składnia

```cpp
[ importidl(idl_file) ];
```

### <a name="parameters"></a>Parametry

*idl_file*<br/>
Określa nazwę pliku. idl, który ma zostać scalony z plikiem. idl, który zostanie wygenerowany dla aplikacji.

## <a name="remarks"></a>Uwagi

Atrybut **importidl** C++ umieszcza sekcję poza blokiem biblioteki (w *idl_file*) w wygenerowanym przez program pliku IDL i sekcji biblioteki (w *idl_file*) do sekcji Biblioteka wygenerowanego pliku IDL programu.

Możesz użyć **importidl**, na przykład, jeśli chcesz użyć ręcznie zakodowanego pliku. idl z wygenerowanym plikiem. idl.

## <a name="example"></a>Przykład

```cpp
// cpp_attr_ref_importidl.cpp
// compile with: /LD
[module(name="MyLib")];
[importidl("import.idl")];
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Dowolnym miejscu|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|None|
|**Nieprawidłowe atrybuty**|None|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty kompilatora](compiler-attributes.md)<br/>
[Oddzielne atrybuty](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importlib](importlib.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)
