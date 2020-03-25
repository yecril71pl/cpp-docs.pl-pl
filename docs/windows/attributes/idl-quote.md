---
title: idl_quote (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.idl_quote
helpviewer_keywords:
- idl_quote attribute
ms.assetid: a370e1b7-948b-4e67-9a25-58facf24e4c9
ms.openlocfilehash: 4b05da6d237d71e0cc645ad0f626f75ecd85c827
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168032"
---
# <a name="idl_quote"></a>idl_quote

Umożliwia korzystanie z konstrukcji IDL, które nie są obsługiwane w bieżącej wersji wizualizacji C++ i są przekazywane do wygenerowanego pliku IDL.

## <a name="syntax"></a>Składnia

```cpp
[ idl_quote(text) ]
```

### <a name="parameters"></a>Parametry

*Opis*<br/>
Nazwa atrybutu, który ma zostać przekazany przez C++ kompilator firmy Microsoft do wygenerowanego pliku IDL bez zwrócenia błędu kompilatora.

## <a name="remarks"></a>Uwagi

Jeśli atrybut **idl_quote** C++ jest używany jako atrybut autonomiczny (z średnikiem po nawiasie zamykającym), *tekst* zostanie umieszczony w scalonym pliku. idl zgodnie z oczekiwaniami. Jeśli **idl_quote** jest używany w symbolu, *tekst* jest umieszczany w bloku atrybutu dla tego symbolu.

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

Ten kod powoduje, że `MYFLOT` i `MYDUB` i wpis *tekstowy* , który ma zostać umieszczony w wygenerowanym pliku IDL. *Nazwa* parametru wymusza umieszczenie *tekstu* przed dowolnymi odwołaniami do *nazwy* w wygenerowanym pliku IDL. Parametr *zależności* wymusza umieszczenie definicji listy zależności przed *tekstem* w wygenerowanym pliku IDL.

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
[Oddzielne atrybuty](stand-alone-attributes.md)
