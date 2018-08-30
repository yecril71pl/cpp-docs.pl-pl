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
ms.openlocfilehash: 9fc3be9fb25b6593f4b69f846394544b7b7d756a
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43220468"
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

*Nazwa*  
Zdefiniowana przez użytkownika nazwa dla bloku kodu, który będzie wyświetlany w pliku .idl.

*Parametr DllName* (opcjonalnie)  
Plik .dll, który zawiera eksportu.

*Identyfikator UUID* (opcjonalnie)  
Unikatowy identyfikator.

*HelpString —* (opcjonalnie)  
Ciąg znaków używany do opisania biblioteki typów.

*helpstringcontext —* (opcjonalnie)  
Identyfikator tematu pomocy w pliku hlp lub chm.

*helpcontext —* (opcjonalnie)  
Identyfikator pomocy dla tego typu biblioteki.

*ukryte* (opcjonalnie)  
Parametr, który zapobiega wyświetlaniu w bibliotece. Zobacz [ukryte](/windows/desktop/Midl/hidden) atrybutu MIDL, aby uzyskać więcej informacji.

*ograniczone* (opcjonalnie)  
Elementy członkowskie biblioteki nie można wywołać arbitralnie. Zobacz [ograniczeniami](/windows/desktop/Midl/restricted) atrybutu MIDL, aby uzyskać więcej informacji.

*Deklaracja funkcji*  
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

[Atrybuty IDL](../windows/idl-attributes.md)  
[Oddzielne atrybuty](../windows/stand-alone-attributes.md)  
[entry](../windows/entry.md)  