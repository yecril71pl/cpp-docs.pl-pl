---
title: importidl — (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.importidl
helpviewer_keywords:
- importidl attribute
ms.assetid: 4b0a4b55-6c57-4e6e-bc7b-a12cc8063941
ms.openlocfilehash: 9db62d4f2a36b8cc0592c924b113077a758915c0
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59029917"
---
# <a name="importidl"></a>importidl

Wstawia pliku .idl określony w pliku .idl wygenerowany.

## <a name="syntax"></a>Składnia

```cpp
[ importidl(idl_file) ];
```

### <a name="parameters"></a>Parametry

*idl_file*<br/>
Określa nazwę pliku .idl, którego chcesz scalić z pliku .idl, którego zostanie wygenerowany dla aplikacji.

## <a name="remarks"></a>Uwagi

**Importidl —** C++ atrybut umieszcza sekcji poza blokiem biblioteki (w *idl_file*) w pliku .idl wygenerowanego programu i w sekcji biblioteki (w *idl_file*) w sekcji biblioteki w pliku .idl wygenerowanego programu.

Możesz chcieć użyć **importidl —**, na przykład, aby za pomocą pliku .idl wygenerowany przy użyciu pliku .idl kodowane ręcznie.

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
|**Dotyczy**|Dowolne miejsce|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty kompilatora](compiler-attributes.md)<br/>
[Oddzielne atrybuty](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importlib](importlib.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)