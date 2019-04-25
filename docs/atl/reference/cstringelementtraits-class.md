---
title: Klasa CStringElementTraits
ms.date: 11/04/2016
f1_keywords:
- CStringElementTraits
- CSTRINGT/ATL::CStringElementTraits
- CSTRINGT/ATL::CStringElementTraits::INARGTYPE
- CSTRINGT/ATL::CStringElementTraits::OUTARGTYPE
- CSTRINGT/ATL::CStringElementTraits::CompareElements
- CSTRINGT/ATL::CStringElementTraits::CompareElementsOrdered
- CSTRINGT/ATL::CStringElementTraits::CopyElements
- CSTRINGT/ATL::CStringElementTraits::Hash
- CSTRINGT/ATL::CStringElementTraits::RelocateElements
helpviewer_keywords:
- CStringElementTraits class
ms.assetid: 74d7134b-099d-4455-bf91-3e68ccbf95bc
ms.openlocfilehash: 80efd4dbc4ff0541e083ed61bed872d5e69c7a74
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62277451"
---
# <a name="cstringelementtraits-class"></a>Klasa CStringElementTraits

Ta klasa udostępnia statyczne funkcje używane przez klasy kolekcji przechowywania `CString` obiektów.

## <a name="syntax"></a>Składnia

```
template <typename T>
class CStringElementTraits
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych, które mają być przechowywane w kolekcji.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|[CStringElementTraits::INARGTYPE](#inargtype)|Typ danych na potrzeby dodawania elementów do obiektu klasy kolekcji.|
|[CStringElementTraits::OUTARGTYPE](#outargtype)|Typ danych używany do pobierania elementów z obiektu klasy kolekcji.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStringElementTraits::CompareElements](#compareelements)|(Statyczny) Wywołaj tę funkcję, aby porównać dwa elementy ciągu dla równości.|
|[CStringElementTraits::CompareElementsOrdered](#compareelementsordered)|(Statyczny) Wywołaj tę funkcję, aby porównać dwa elementy ciągu.|
|[CStringElementTraits::CopyElements](#copyelements)|(Statyczny) Wywołaj tę funkcję, aby skopiować `CString` elementów przechowywanych w obiekcie klasy kolekcji.|
|[CStringElementTraits::Hash](#hash)|(Statyczny) Wywołaj tę funkcję, aby obliczyć wartość skrótu dla elementu dany ciąg znaków.|
|[CStringElementTraits::RelocateElements](#relocateelements)|(Statyczny) Wywołaj tę funkcję, aby przenieść `CString` elementów przechowywanych w obiekcie klasy kolekcji.|

## <a name="remarks"></a>Uwagi

Ta klasa udostępnia funkcje statyczne, kopiowanie, przenoszenie i porównywanie ciągów, a także do tworzenia wartości skrótu. Te funkcje są przydatne w przypadku korzystania z klasy kolekcji do przechowywania danych w ciągu. Użyj [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md) podczas porównania bez uwzględniania wielkości liter są wymagane. Użyj [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md) kiedy mają będzie traktowane jako odwołania do obiektów w postaci ciągów.

Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** cstringt.h

##  <a name="compareelements"></a>  CStringElementTraits::CompareElements

Wywołaj tę funkcję statycznej, aby porównać dwa elementy ciągu dla równości.

```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
Pierwszy ciąg elementu.

*str2*<br/>
Drugi ciąg elementu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli elementy są równe, wartość false w przeciwnym razie.

##  <a name="compareelementsordered"></a>  CStringElementTraits::CompareElementsOrdered

Wywołaj tę funkcję statycznej, aby porównać dwa elementy ciągu.

```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
Pierwszy ciąg elementu.

*str2*<br/>
Drugi ciąg elementu.

### <a name="return-value"></a>Wartość zwracana

Zero, jeśli ciągi są identyczne, < 0 Jeśli *str1* jest mniejsza niż *str2*, lub > 0 Jeśli *str1* jest większa niż *str2*. [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare) metoda służy do przeprowadzania porównania.

##  <a name="copyelements"></a>  CStringElementTraits::CopyElements

Wywołaj tę funkcję statycznej, aby skopiować `CString` elementów przechowywanych w obiekcie klasy kolekcji.

```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>Parametry

*pDest*<br/>
Wskaźnik do pierwszego elementu, który będzie otrzymywać dane skopiowane.

*pSrc*<br/>
Wskaźnik do pierwszego elementu, aby skopiować.

*nElements*<br/>
Liczba elementów do skopiowania.

### <a name="remarks"></a>Uwagi

Elementy źródłowe i docelowe nie powinny nakładać się na.

##  <a name="hash"></a>  CStringElementTraits::Hash

Wywołaj tę funkcję statycznej, aby obliczyć wartość skrótu dla elementu dany ciąg znaków.

```
static ULONG Hash(INARGTYPE str);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Element ciągu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość skrótu obliczane przy użyciu zawartości ciągu.

##  <a name="inargtype"></a>  CStringElementTraits::INARGTYPE

Typ danych na potrzeby dodawania elementów do obiektu klasy kolekcji.

```
typedef T::PCXSTR INARGTYPE;
```

##  <a name="outargtype"></a>  CStringElementTraits::OUTARGTYPE

Typ danych używany do pobierania elementów z obiektu klasy kolekcji.

```
typedef T& OUTARGTYPE;
```

##  <a name="relocateelements"></a>  CStringElementTraits::RelocateElements

Wywołaj tę funkcję statycznego przenosić `CString` elementów przechowywanych w obiekcie klasy kolekcji.

```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>Parametry

*pDest*<br/>
Wskaźnik do pierwszego elementu, który będzie otrzymywać dane przenoszone.

*pSrc*<br/>
Wskaźnik do pierwszego elementu przenosić.

*nElements*<br/>
Liczba elementów do przeniesienia.

### <a name="remarks"></a>Uwagi

Ta funkcja statyczna wywołuje [memmove](../../c-runtime-library/reference/memmove-wmemmove.md), który jest wystarczające dla większości typów danych. Jeśli obiektów jest przenoszony zawierają wskaźniki do ich własnych elementów członkowskich, ta funkcja statyczna muszą zostać zastąpiona.

## <a name="see-also"></a>Zobacz także

[Klasa CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)<br/>
[Klasa CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
