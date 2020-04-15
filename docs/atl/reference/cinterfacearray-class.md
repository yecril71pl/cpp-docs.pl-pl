---
title: Klasa CInterfaceArray
ms.date: 11/04/2016
f1_keywords:
- CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray::CInterfaceArray
helpviewer_keywords:
- CInterfaceArray class
ms.assetid: 1f29cf66-a086-4a7b-b6a8-64f73da39f79
ms.openlocfilehash: e6efe31989b06f0977ecff156a8f64053dc64ad1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326800"
---
# <a name="cinterfacearray-class"></a>Klasa CInterfaceArray

Ta klasa zawiera metody przydatne podczas konstruowania tablicy wskaźników interfejsu COM.

## <a name="syntax"></a>Składnia

```
template <class I, const IID* piid=& __uuidof(I)>
class CInterfaceArray :
   public CAtlArray<ATL::CComQIPtr<I, piid>,
                    CComQIPtrElementTraits<I, piid>>
```

#### <a name="parameters"></a>Parametry

*I*<br/>
Interfejs COM określający typ wskaźnika do przechowywania.

*piid*<br/>
Wskaźnik do identyfikatora *I*.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CInterfaceArray::CInterfaceArray](#cinterfacearray)|Konstruktor tablicy interfejsu.|

## <a name="remarks"></a>Uwagi

Ta klasa zawiera konstruktora i metody pochodne do tworzenia tablicy wskaźników interfejsu COM. Użyj [CInterfaceList,](../../atl/reference/cinterfacelist-class.md) gdy lista jest wymagana.

Aby uzyskać więcej informacji, zobacz [ATL Collection Classes](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CAtlArray`

`CInterfaceArray`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

## <a name="cinterfacearraycinterfacearray"></a><a name="cinterfacearray"></a>CInterfaceArray::CInterfaceArray

Konstruktor.

```
CInterfaceArray() throw();
```

### <a name="remarks"></a>Uwagi

Inicjuje tablicę inteligentnych wskaźników.

## <a name="see-also"></a>Zobacz też

[Klasa CAtlArray](../../atl/reference/catlarray-class.md)<br/>
[Klasa CComQIPtr](../../atl/reference/ccomqiptr-class.md)<br/>
[Klasa CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
