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
ms.openlocfilehash: 078cfd5ff93bfcd8acc747904ea05e6a2e762bc1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330624"
---
# <a name="cstringelementtraits-class"></a>Klasa CStringElementTraits

Ta klasa zawiera funkcje statyczne `CString` używane przez klasy kolekcji przechowywania obiektów.

## <a name="syntax"></a>Składnia

```
template <typename T>
class CStringElementTraits
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych, które mają być przechowywane w kolekcji.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

|Nazwa|Opis|
|----------|-----------------|
|[CStringElementTraits::INARGTYPE](#inargtype)|Typ danych do dodania elementów do obiektu klasy kolekcji.|
|[CStringElementTraits::OUTARGTYPE](#outargtype)|Typ danych do użycia do pobierania elementów z obiektu klasy kolekcji.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStringElementTraits::CompareElements](#compareelements)|(Statyczne) Wywołanie tej funkcji, aby porównać dwa elementy ciągu dla równości.|
|[CStringElementTraits::CompareElementsOrdered](#compareelementsordered)|(Statyczne) Wywołanie tej funkcji, aby porównać dwa elementy ciągu.|
|[CStringElementTraits::CopyElements](#copyelements)|(Statyczne) Wywołanie tej `CString` funkcji, aby skopiować elementy przechowywane w obiekcie klasy kolekcji.|
|[CStringElementTraits::Hash](#hash)|(Statyczne) Wywołanie tej funkcji, aby obliczyć wartość mieszania dla danego elementu ciągu.|
|[CStringElementTraits::RelocateElements](#relocateelements)|(Statyczne) Wywołanie tej funkcji, aby przenieść `CString` elementy przechowywane w obiekcie klasy kolekcji.|

## <a name="remarks"></a>Uwagi

Ta klasa udostępnia funkcje statyczne do kopiowania, przenoszenia i porównywania ciągów oraz do tworzenia wartości mieszania. Te funkcje są przydatne podczas korzystania z klasy kolekcji do przechowywania danych opartych na ciągu. Użyj [CStringElementTraitsI,](../../atl/reference/cstringelementtraitsi-class.md) gdy wymagane są porównania bez uwzględniania wielkości liter. Użyj [CStringRefElementTraits,](../../atl/reference/cstringrefelementtraits-class.md) gdy obiekty ciągu mają być traktowane jako odwołania.

Aby uzyskać więcej informacji, zobacz [ATL Collection Classes](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** cstringt.h

## <a name="cstringelementtraitscompareelements"></a><a name="compareelements"></a>CStringElementTraits::CompareElements

Wywołanie tej funkcji statycznej, aby porównać dwa elementy ciągu dla równości.

```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
Pierwszy element ciągu.

*str2*<br/>
Drugi element ciągu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli elementy są równe, false inaczej.

## <a name="cstringelementtraitscompareelementsordered"></a><a name="compareelementsordered"></a>CStringElementTraits::CompareElementsOrdered

Wywołanie tej funkcji statycznej, aby porównać dwa elementy ciągu.

```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
Pierwszy element ciągu.

*str2*<br/>
Drugi element ciągu.

### <a name="return-value"></a>Wartość zwracana

Zero, jeśli ciągi są identyczne, < 0, jeśli *str1* jest mniejsza niż *str2*lub > 0, jeśli *str1* jest większa niż *str2*. [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare) Metoda jest używana do wykonywania porównań.

## <a name="cstringelementtraitscopyelements"></a><a name="copyelements"></a>CStringElementTraits::CopyElements

Wywołanie tej funkcji `CString` statycznej, aby skopiować elementy przechowywane w obiekcie klasy kolekcji.

```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>Parametry

*pDest (właśc.*<br/>
Wskaźnik do pierwszego elementu, który otrzyma skopiowane dane.

*Psrc*<br/>
Wskaźnik do pierwszego elementu do skopiowania.

*nElementy*<br/>
Liczba elementów do skopiowania.

### <a name="remarks"></a>Uwagi

Elementy źródłowe i docelowe nie powinny nakładać się na siebie.

## <a name="cstringelementtraitshash"></a><a name="hash"></a>CStringElementTraits::Hash

Wywołanie tej funkcji statycznej, aby obliczyć wartość mieszania dla danego elementu ciągu.

```
static ULONG Hash(INARGTYPE str);
```

### <a name="parameters"></a>Parametry

*Str*<br/>
Element ciągu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość mieszania obliczoną przy użyciu zawartości ciągu.

## <a name="cstringelementtraitsinargtype"></a><a name="inargtype"></a>CStringElementTraits::INARGTYPE

Typ danych do dodania elementów do obiektu klasy kolekcji.

```
typedef T::PCXSTR INARGTYPE;
```

## <a name="cstringelementtraitsoutargtype"></a><a name="outargtype"></a>CStringElementTraits::OUTARGTYPE

Typ danych do użycia do pobierania elementów z obiektu klasy kolekcji.

```
typedef T& OUTARGTYPE;
```

## <a name="cstringelementtraitsrelocateelements"></a><a name="relocateelements"></a>CStringElementTraits::RelocateElements

Wywołanie tej funkcji statycznej, aby przenieść `CString` elementy przechowywane w obiekcie klasy kolekcji.

```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>Parametry

*pDest (właśc.*<br/>
Wskaźnik do pierwszego elementu, który otrzyma przeniesione dane.

*Psrc*<br/>
Wskaźnik do pierwszego elementu do przeniesienia.

*nElementy*<br/>
Liczba elementów do przeniesienia.

### <a name="remarks"></a>Uwagi

Ta funkcja statyczna wywołuje [memmove](../../c-runtime-library/reference/memmove-wmemmove.md), co jest wystarczające dla większości typów danych. Jeśli obiekty są przenoszone zawierają wskaźniki do własnych elementów członkowskich, ta funkcja statyczna będzie musiał zostać zastąpiona.

## <a name="see-also"></a>Zobacz też

[Klasa CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)<br/>
[Klasa CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
