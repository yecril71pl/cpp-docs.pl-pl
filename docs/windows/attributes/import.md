---
title: Import (C++ atrybut com)
ms.date: 10/03/2018
f1_keywords:
- vc-attr.import
helpviewer_keywords:
- import attribute
ms.assetid: ebf07cae-39fb-4047-8b57-54af0a9a83de
ms.openlocfilehash: f2a0aa9a68c081e83a7a5278aa37a7fddac85416
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166839"
---
# <a name="import"></a>import

Określa inny plik IDL, ODL lub nagłówkowy zawierający definicje, które chcesz odwołać z głównego IDL.

## <a name="syntax"></a>Składnia

```cpp
[ import(
   idl_file
) ];
```

### <a name="parameters"></a>Parametry

*idl_file*<br/>
Nazwa pliku. idl, który ma zostać zaimportowany do biblioteki typów w bieżącym projekcie.

## <a name="remarks"></a>Uwagi

Atrybut **Import** C++ powoduje umieszczenie instrukcji `#import` poniżej instrukcji `import "docobj.idl"` w wygenerowanym pliku IDL. Atrybut **Import** ma takie same funkcje jak atrybut [Import](/windows/win32/Midl/import) MIDL.

Atrybut **Import** umieszcza tylko określony plik w pliku. idl, który zostanie wygenerowany przez projekt; atrybut **Import** nie pozwala na wywoływanie konstrukcji w określonym pliku z kodu źródłowego w projekcie.  Aby wywołać konstrukcje w określonym pliku z kodu źródłowego w projekcie, użyj [#import](../../preprocessor/hash-import-directive-cpp.md) i atrybutu `embedded_idl` lub można dołączyć plik h dla *idl_file*, jeśli istnieje plik. h.

## <a name="example"></a>Przykład

Następujący kod:

```cpp
// cpp_attr_ref_import.cpp
// compile with: /LD
[module(name="MyLib")];
[import(import.idl)];
```

generuje następujący kod w wygenerowanym pliku IDL:

```
import "docobj.idl";
import "import.idl";

[ uuid(EED3644C-8488-3ECD-BA97-147DB3CDB499), version(1.0) ]
library MyLib {
   importlib("stdole2.tlb");
   importlib("olepro32.dll");
...
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

[Atrybuty IDL](idl-attributes.md)<br/>
[Oddzielne atrybuty](stand-alone-attributes.md)<br/>
[importidl](importidl.md)<br/>
[importlib](importlib.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)
