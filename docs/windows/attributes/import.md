---
title: Importowanie (atrybut C++ COM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.import
dev_langs:
- C++
helpviewer_keywords:
- import attribute
ms.assetid: ebf07cae-39fb-4047-8b57-54af0a9a83de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a0509f6c1292ee7bb2e1ba97d1f75c626f3b0761
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789754"
---
# <a name="import"></a>import

Określa innego pliku .idl, .odl — lub nagłówek zawierający definicje, który ma zostać utworzone odwołanie z sieci głównego pliku IDL.

## <a name="syntax"></a>Składnia

```cpp
[ import(
   idl_file
) ];
```

### <a name="parameters"></a>Parametry

*idl_file*<br/>
Nazwa pliku .idl, który ma zostać zaimportowany do biblioteki typów w bieżącym projekcie.

## <a name="remarks"></a>Uwagi

**Zaimportować** atrybut C++ powoduje `#import` instrukcję, aby umieszczona pod `import "docobj.idl"` instrukcja w pliku .idl wygenerowany. **Zaimportować** atrybut ma taką samą funkcjonalność jak [zaimportować](/windows/desktop/Midl/import) atrybutów w MIDL.

**Zaimportować** atrybutu tylko umieszcza określonego pliku w pliku .idl, który zostanie wygenerowany w projekcie; **zaimportować** atrybutu nie zezwala na wywołania konstrukcje w określonym pliku z kodem źródłowym w projekcie.  Aby wywołać konstrukcje w określonym pliku z kodem źródłowym w projekcie, albo użyć [#import](../../preprocessor/hash-import-directive-cpp.md) i `embedded_idl` lub atrybut może znajdować się plik .h dla *idl_file*, jeśli istnieje plik .h klasy.

## <a name="example"></a>Przykład

Poniższy kod:

```cpp
// cpp_attr_ref_import.cpp
// compile with: /LD
[module(name="MyLib")];
[import(import.idl)];
```

generuje następujący kod w pliku .idl wygenerowanego:

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
|**Dotyczy**|Dowolne miejsce|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Oddzielne atrybuty](stand-alone-attributes.md)<br/>
[importidl](importidl.md)<br/>
[importlib](importlib.md)<br/>
[include](include-cpp.md)<br/>
[includelib —](includelib-cpp.md)  