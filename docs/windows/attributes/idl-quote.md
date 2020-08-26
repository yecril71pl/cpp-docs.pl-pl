---
title: idl_quote (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.idl_quote
helpviewer_keywords:
- idl_quote attribute
ms.assetid: a370e1b7-948b-4e67-9a25-58facf24e4c9
ms.openlocfilehash: 1d0aa80f64593ed347720b84e4059a0c32dce4be
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844239"
---
# <a name="idl_quote"></a>idl_quote

Umożliwia korzystanie z konstrukcji IDL, które nie są obsługiwane w bieżącej wersji Visual C++ i umożliwiają przekazywanie ich do wygenerowanego pliku IDL.

## <a name="syntax"></a>Składnia

```cpp
[ idl_quote(text) ]
```

### <a name="parameters"></a>Parametry

*Opis*<br/>
Nazwa atrybutu, który ma zostać przekazany przez kompilator języka Microsoft C++ do wygenerowanego pliku IDL bez zwrócenia błędu kompilatora.

## <a name="remarks"></a>Uwagi

Jeśli atrybut **idl_quote** C++ jest używany jako atrybut autonomiczny (średnik po nawiasie zamykającym), *tekst* zostanie umieszczony w scalonym pliku. idl jako. Jeśli **idl_quote** jest używany w symbolu, *tekst* jest umieszczany w bloku atrybutu dla tego symbolu.

## <a name="example"></a>Przykład

Poniższy kod przedstawia sposób określenia nieobsługiwanego atrybutu (przy użyciu **w**, który jest obsługiwany) oraz sposobu definiowania niezdefiniowanej konstrukcji IDL i korzystania z niej:

```cpp
// cpp_attr_ref_idl_quote.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLibrary")];

[export]
struct MYFLOT {
   int i;
};

[export]
struct MYDUB {
   int i;
};

[idl_quote("typedef union _S1_TYPE switch (long l1) U1_TYPE { case 1024: \
struct MYFLOT f1; case 2048: struct MYDUB d2; } S1_TYPE;") ];

typedef struct _S1_TYPE {
   long l1;

union {
   MYFLOT f1; MYDUB d2; } U1_TYPE;
} S1_TYPE;

[uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA"), object]
__interface IStatic{
   HRESULT Func1([idl_quote("in")] int i);
   HRESULT func( S1_TYPE* myStruct );
};
```

Ten kod powoduje `MYFLOT` i `MYDUB` i wpis *tekstowy* , który ma zostać umieszczony w wygenerowanym pliku IDL. *Nazwa* parametru wymusza umieszczenie *tekstu* przed dowolnymi odwołaniami do *nazwy* w wygenerowanym pliku IDL. Parametr *zależności* wymusza umieszczenie definicji listy zależności przed *tekstem* w wygenerowanym pliku IDL.

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
[Atrybuty autonomiczne](stand-alone-attributes.md)
