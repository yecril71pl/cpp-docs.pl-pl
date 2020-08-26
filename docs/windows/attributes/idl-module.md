---
title: idl_module (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.idl_module
helpviewer_keywords:
- idl_module attribute
ms.assetid: 3578b337-e38a-4334-b747-15404c02dbc0
ms.openlocfilehash: 651d2e133d7ef08fce48feded1b7a5aff458adb1
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845227"
---
# <a name="idl_module"></a>idl_module

Określa punkt wejścia w pliku dll.

## <a name="syntax"></a>Składnia

```cpp
[ idl_module (name=module_name, dllname=dll, uuid="uuid", helpstring="help text", helpstringcontext=helpcontextID, helpcontext=helpcontext, hidden, restricted) ]
function declaration
```

### <a name="parameters"></a>Parametry

*Nazwij*<br/>
Zdefiniowana przez użytkownika nazwa bloku kodu, który będzie wyświetlany w pliku IDL.

*nazwa_pliku_dll*<br/>
Obowiązkowe Plik. dll, który zawiera eksport.

*uuid*<br/>
Obowiązkowe Unikatowy identyfikator.

*helpstring*<br/>
Obowiązkowe Ciąg znaków używany do opisywania biblioteki typów.

*helpstringcontext*<br/>
Obowiązkowe Identyfikator tematu pomocy w pliku HLP lub chm.

*helpcontext*<br/>
Obowiązkowe Identyfikator pomocy dla tej biblioteki typów.

*hidden*<br/>
Obowiązkowe Parametr, który uniemożliwia wyświetlenie biblioteki. Aby uzyskać więcej informacji, zobacz [ukryty](/windows/win32/Midl/hidden) atrybut MIDL.

*podlega*<br/>
Obowiązkowe Nie można arbitralnie wywołać elementów członkowskich biblioteki. Aby uzyskać więcej informacji, zobacz atrybut MIDL z [ograniczeniami](/windows/win32/Midl/restricted) .

*Deklaracja funkcji*<br/>
Funkcja, która zostanie zdefiniowana.

## <a name="remarks"></a>Uwagi

Atrybut **idl_module** C++ umożliwia określenie punktu wejścia w pliku dll, który umożliwia importowanie z pliku dll.

Atrybut **idl_module** ma funkcje podobne do atrybutu MIDL [modułu](/windows/win32/Midl/module) .

Można eksportować elementy z obiektu COM, który można wyeksportować z pliku DLL przez umieszczenie punktu wejścia biblioteki DLL w bloku biblioteki pliku. idl.

Należy używać **idl_module** w dwóch krokach. Najpierw należy zdefiniować parę nazwa/Biblioteka DLL. Następnie, korzystając z **idl_module** , aby określić punkt wejścia, określ nazwę i wszelkie dodatkowe atrybuty.

## <a name="example"></a>Przykład

Poniższy kod pokazuje, jak używać atrybutu **idl_module** :

```cpp
// cpp_attr_ref_idl_module.cpp
// compile with: /LD
[idl_quote("midl_pragma warning(disable:2461)")];
[module(name="MyLibrary"), idl_module(name="MyLib", dllname="xxx.dll")];
[idl_module(name="MyLib"), entry(4), usesgetlasterror]
void FuncName(int i);
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

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty autonomiczne](stand-alone-attributes.md)<br/>
[Autotekstu](entry.md)
