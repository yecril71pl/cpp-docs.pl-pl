---
title: Klasa CSimpleArrayEqualHelperFalse
ms.date: 11/04/2016
f1_keywords:
- CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse::IsEqual
helpviewer_keywords:
- CSimpleArrayEqualHelperFalse class
ms.assetid: 6918af6f-d23d-49eb-8482-c44272f5ffeb
ms.openlocfilehash: 91987d369291a092b6dfb5f7db9ca8ba1434a7cc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594912"
---
# <a name="csimplearrayequalhelperfalse-class"></a>Klasa CSimpleArrayEqualHelperFalse

Ta klasa jest pomocnika dla [CSimpleArray](../../atl/reference/csimplearray-class.md) klasy.

## <a name="syntax"></a>Składnia

```
template <class T>
class CSimpleArrayEqualHelperFalse
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasy pochodnej.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSimpleArrayEqualHelperFalse::IsEqual](#isequal)|(Statyczny) Zwraca wartość false.|

## <a name="remarks"></a>Uwagi

Ta klasa cech jest uzupełnieniem `CSimpleArray` klasy. IT zawsze zwraca wartość false, a ponadto wywoła `ATLASSERT` z nieprawidłowym argumentem wartość false, jeśli nigdy nie jest wywoływany. W sytuacjach, w którym testu równości nie jest wystarczająco zdefiniowana ta klasa umożliwia tablica zawierająca elementy, aby działać prawidłowo w przypadku większości metod, ale nie działać w sposób dobrze zdefiniowanych dla metod, które są zależne od porównań, takich jak [CSimpleArray:: Znajdź](../../atl/reference/csimplearray-class.md#find).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsimpcoll.h

##  <a name="isequal"></a>  CSimpleArrayEqualHelperFalse::IsEqual

Zwraca wartość false.

```
static bool IsEqual(const T&, const T&);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość false.

### <a name="remarks"></a>Uwagi

Ta metoda zawsze zwraca wartość false i wywoła `ATLASSERT` z nieprawidłowym argumentem false, jeśli przywoływany. Celem `CSimpleArrayEqualHelperFalse::IsEqual` jest wymuszenie metod, które się nie powieść w dobrze zdefiniowany sposób w przypadku równości testy nie zostały odpowiednio zdefiniowane za pomocą porównania.

## <a name="see-also"></a>Zobacz też

[Klasa CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
