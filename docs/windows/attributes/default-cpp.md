---
title: Default (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.default
helpviewer_keywords:
- default attribute
- attributes [C#], default attribute
- defaults, default attribute
ms.assetid: 0cdca716-1ba8-46d7-9399-167e55492870
ms.openlocfilehash: 291e16ad0967acd1869874fcc9fa6eb5529e4b44
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501679"
---
# <a name="default-c"></a>default (C++)

Wskazuje, że niestandardowe lub dispinterface zdefiniowane w ramach klasy coclass reprezentuje domyślny interfejs programistyczny.

## <a name="syntax"></a>Składnia

```cpp
[ default(interface1, interface2) ]
```

### <a name="parameters"></a>Parametry

*interface1*<br/>
Domyślny interfejs, który zostanie udostępniony dla środowisk skryptów, które tworzą obiekt na podstawie klasy zdefiniowanej przy użyciu atrybutu **domyślnego** .

Jeśli nie określono żadnego interfejsu domyślnego, domyślnie używane jest pierwsze wystąpienie interfejsu nieźródłowego.

*interface2*<br/>
Obowiązkowe Domyślny interfejs źródłowy. Należy również określić ten interfejs przy użyciu atrybutu [Source](source-cpp.md) .

Jeśli nie określono żadnego domyślnego interfejsu źródłowego, domyślnie używany jest pierwszy interfejs źródłowy.

## <a name="remarks"></a>Uwagi

**Domyślny** C++ atrybut ma taką samą funkcjonalność jak [domyślny](/windows/win32/Midl/default) atrybut MIDL. **Domyślny** atrybut jest również używany z atrybutem [Case](case-cpp.md) .

## <a name="example"></a>Przykład

Poniższy kod pokazuje, jak **domyślny** jest używany w definicji klasy coclass, aby określić `ICustomDispatch` jako domyślny interfejs programowania:

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

Atrybut [Source](source-cpp.md) zawiera również przykład sposobu użycia wartości **domyślnej**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Klasa**, **Struktura**, składowa danych|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|**Klasa coclass** (w przypadku zastosowania do **klasy** lub **struktury**)|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[coclass](coclass.md)