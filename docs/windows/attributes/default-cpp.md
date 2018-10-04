---
title: domyślne (C++ COM atrybut) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.default
dev_langs:
- C++
helpviewer_keywords:
- default attribute
- attributes [C#], default attribute
- defaults, default attribute
ms.assetid: 0cdca716-1ba8-46d7-9399-167e55492870
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5fb7f205ccdf78e1ef64e2ba2c132e3c2b6b6000
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789781"
---
# <a name="default-c"></a>default (C++)

Wskazuje, że niestandardowe lub zdefiniowane w obrębie klasy coclass dispinterface reprezentuje domyślny interfejs programowania.

## <a name="syntax"></a>Składnia

```cpp
[ default(interface1, interface2) ]
```

### <a name="parameters"></a>Parametry

*interface1*<br/>
Domyślny interfejs, które będą dostępne do wykonywania skryptów środowiska, w których utworzenia obiektu na podstawie klasy zdefiniowane za pomocą **domyślne** atrybutu.

Jeśli nie domyślny interfejs jest określony, pierwsze wystąpienie interfejsu nonsource jest używany jako domyślny.

*interface2*<br/>
(Opcjonalnie) Domyślnym interfejsie źródła. Należy także określić ten interfejs, za pomocą [źródła](source-cpp.md) atrybutu.

Jeśli nie domyślnym interfejsie źródła jest określony, pierwszy interfejs źródłowy jest używany jako domyślny.

## <a name="remarks"></a>Uwagi

**Domyślne** atrybut C++ ma taką samą funkcjonalność jak [domyślne](/windows/desktop/Midl/default) atrybutów w MIDL. **Domyślne** również zostanie użyty atrybut [przypadek](case-cpp.md) atrybutu.

## <a name="example"></a>Przykład

Poniższy kod przedstawia sposób **domyślne** służy do określania, w definicji klasy coclass `ICustomDispatch` jako domyślny interfejs programowania:

```cpp
// cpp_attr_ref_default.cpp
// compile with: /LD
#include "windows.h"
[module(name="MyLibrary")];

[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]
__interface ICustom {
   HRESULT Custom([in] long l, [out, retval] long *pLong);
};

[dual, uuid("9E66A291-4365-11D2-A997-00C04FA37DDB")]
__interface IDual {
   HRESULT Dual([in] long l, [out, retval] long *pLong);
};

[object, uuid("9E66A293-4365-11D2-A997-00C04FA37DDB")]
__interface ICustomDispatch : public IDispatch {
   HRESULT Dispatch([in] long l, [out, retval] long *pLong);
};

[   coclass, default(ICustomDispatch), source(IDual), uuid("9E66A294-4365-11D2-A997-00C04FA37DDB")  
]
class CClass : public ICustom, public IDual, public ICustomDispatch {
   HRESULT Custom(long l, long *pLong) { return(S_OK); }
   HRESULT Dual(long l, long *pLong) { return(S_OK); }
   HRESULT Dispatch(long l, long *pLong) { return(S_OK); }
};

int main() {
#if 0 // Can't instantiate without implementations of IUnknown/IDispatch
   CClass *pClass = new CClass;

   long llong;

   pClass->custom(1, &llong);
   pClass->dual(1, &llong);
   pClass->dispinterface(1, &llong);
   pClass->dispatch(1, &llong);

   delete pClass;
#endif
   return(0);
}
```

[Źródła](source-cpp.md) atrybut zawiera również przykład sposobu użycia **domyślne**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Klasa**, **struktury**, element członkowski danych|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|**Klasa coclass** (po zastosowaniu do **klasy** lub **struktury**)|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[coclass](coclass.md)  