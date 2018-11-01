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
ms.openlocfilehash: 64271cbdb634284a5abcdd17b2c14d23a496b3f5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614256"
---
# <a name="cinterfacearray-class"></a>Klasa CInterfaceArray

Ta klasa dostarcza metody przydatne przy konstruowaniu tablicy wskaźników interfejsu COM.

## <a name="syntax"></a>Składnia

```
template <class I, const IID* piid=& __uuidof(I)>
class CInterfaceArray :
   public CAtlArray<ATL::CComQIPtr<I, piid>,
                    CComQIPtrElementTraits<I, piid>>
```

#### <a name="parameters"></a>Parametry

*I*<br/>
Interfejs COM, określając typ wskaźnika, które mają być przechowywane.

*piid*<br/>
Wskaźnik do identyfikatora IID z *I*.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CInterfaceArray::CInterfaceArray](#cinterfacearray)|Konstruktor dla tablicy interfejsu.|

## <a name="remarks"></a>Uwagi

Ta klasa zawiera konstruktora i pochodnej metody tworzenia tablicy wskaźników interfejsu COM. Użyj [CInterfaceList](../../atl/reference/cinterfacelist-class.md) gdy lista jest wymagana.

Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CAtlArray`

`CInterfaceArray`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

##  <a name="cinterfacearray"></a>  CInterfaceArray::CInterfaceArray

Konstruktor.

```
CInterfaceArray() throw();
```

### <a name="remarks"></a>Uwagi

Inicjuje tablicę inteligentnego wskaźnika.

## <a name="see-also"></a>Zobacz też

[Klasa CAtlArray](../../atl/reference/catlarray-class.md)<br/>
[Klasa CComQIPtr](../../atl/reference/ccomqiptr-class.md)<br/>
[Klasa CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
