---
title: importidl (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.importidl
helpviewer_keywords:
- importidl attribute
ms.assetid: 4b0a4b55-6c57-4e6e-bc7b-a12cc8063941
ms.openlocfilehash: 8f3c2c5c67ac216d096d1082814c561698f3f732
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842250"
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

Atrybut **importidl** C++ umieszcza sekcję poza blokiem biblioteki (w *idl_file*) w wygenerowanym przez program pliku IDL i sekcji biblioteki (w *idl_file*) do sekcji Biblioteka wygenerowanego pliku. idl programu.

Możesz użyć **importidl**, na przykład, jeśli chcesz użyć ręcznie zakodowanego pliku. idl z wygenerowanym plikiem. idl.

## <a name="example"></a>Przykład

```cpp
// cpp_attr_ref_importidl.cpp
// compile with: /LD
[module(name="MyLib")];
[importidl("import.idl")];
```

## <a name="requirements"></a>Wymagania

| Kontekst atrybutu | Wartość |
|-|-|
|**Dotyczy**|Dowolne miejsce|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty kompilatora](compiler-attributes.md)<br/>
[Atrybuty autonomiczne](stand-alone-attributes.md)<br/>
[zaimportować](import.md)<br/>
[importlib](importlib.md)<br/>
[być](include-cpp.md)<br/>
[includelib —](includelib-cpp.md)
