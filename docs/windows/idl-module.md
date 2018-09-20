---
title: idl_module | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.idl_module
dev_langs:
- C++
helpviewer_keywords:
- idl_module attribute
ms.assetid: 3578b337-e38a-4334-b747-15404c02dbc0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0539275a09a64e31a9ecad17cab899368701e353
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412219"
---
# <a name="idlmodule"></a>idl_module

Określa punkt wejścia w pliku dll.

## <a name="syntax"></a>Składnia

```cpp
[ idl_module (
   name=module_name,
   dllname=dll,
   uuid="uuid",
   helpstring="help text",
   helpstringcontext=helpcontextID,
   helpcontext=helpcontext,
   hidden,
   restricted
) ]
function declaration
```

### <a name="parameters"></a>Parametry

*Nazwa*<br/>
Zdefiniowana przez użytkownika nazwa dla bloku kodu, który będzie wyświetlany w pliku .idl.

*Parametr DllName*<br/>
(Opcjonalnie) Plik .dll, który zawiera eksportu.

*uuid*<br/>
(Opcjonalnie) Unikatowy identyfikator.

*helpstring*<br/>
(Opcjonalnie) Ciąg znaków używany do opisania biblioteki typów.

*helpstringcontext*<br/>
(Opcjonalnie) Identyfikator tematu pomocy w pliku hlp lub chm.

*helpcontext*<br/>
(Opcjonalnie) Identyfikator pomocy dla tego typu biblioteki.

*hidden*<br/>
(Opcjonalnie) Parametr, który zapobiega wyświetlaniu w bibliotece. Zobacz [ukryte](/windows/desktop/Midl/hidden) atrybutu MIDL, aby uzyskać więcej informacji.

*restricted*<br/>
(Opcjonalnie) Elementy członkowskie biblioteki nie można wywołać arbitralnie. Zobacz [ograniczeniami](/windows/desktop/Midl/restricted) atrybutu MIDL, aby uzyskać więcej informacji.

*Deklaracja funkcji*<br/>
Funkcja, która będą definiować.

## <a name="remarks"></a>Uwagi

**Idl_module** atrybut C++ umożliwia określenie punktu wejścia w pliku .dll, dzięki czemu można zaimportować z pliku dll.

**Idl_module** atrybut ma funkcje podobne do [modułu](/windows/desktop/Midl/module) atrybutów w MIDL.

Możesz wyeksportować nic z obiektu COM, który można eksportować z pliku .dll, umieszczając punkt wejścia biblioteki DLL w bloku biblioteki pliku .idl.

Usługi muszą używać **idl_module** w dwóch krokach. Najpierw należy zdefiniować pary nazwa/DLL. Następnie, kiedy używasz **idl_module** do określonego punktu wejścia, określ nazwę oraz wszelkie dodatkowe atrybuty.

## <a name="example"></a>Przykład

Poniższy kod przedstawia sposób użycia **idl_module** atrybutu:

```cpp
// cpp_attr_ref_idl_module.cpp
// compile with: /LD
[idl_quote("midl_pragma warning(disable:2461)")];
[module(name="MyLibrary"), idl_module(name="MyLib", dllname="xxx.dll")];
[idl_module(name="MyLib"), entry(4), usesgetlasterror]
void FuncName(int i);
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Dowolne miejsce|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](../windows/idl-attributes.md)<br/>
[Oddzielne atrybuty](../windows/stand-alone-attributes.md)<br/>
[entry](../windows/entry.md)  