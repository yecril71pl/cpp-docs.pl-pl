---
title: Klasa CTypedPtrArray
ms.date: 11/04/2016
f1_keywords:
- CTypedPtrArray
- AFXTEMPL/CTypedPtrArray
- AFXTEMPL/CTypedPtrArray::Add
- AFXTEMPL/CTypedPtrArray::Append
- AFXTEMPL/CTypedPtrArray::Copy
- AFXTEMPL/CTypedPtrArray::ElementAt
- AFXTEMPL/CTypedPtrArray::GetAt
- AFXTEMPL/CTypedPtrArray::InsertAt
- AFXTEMPL/CTypedPtrArray::SetAt
- AFXTEMPL/CTypedPtrArray::SetAtGrow
helpviewer_keywords:
- CTypedPtrArray [MFC], Add
- CTypedPtrArray [MFC], Append
- CTypedPtrArray [MFC], Copy
- CTypedPtrArray [MFC], ElementAt
- CTypedPtrArray [MFC], GetAt
- CTypedPtrArray [MFC], InsertAt
- CTypedPtrArray [MFC], SetAt
- CTypedPtrArray [MFC], SetAtGrow
ms.assetid: e3ecdf1a-a889-4156-92dd-ddbd36ccd919
ms.openlocfilehash: 20cf147e955b6b19919f35750b0f46a8b5a67ad0
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752063"
---
# <a name="ctypedptrarray-class"></a>Klasa CTypedPtrArray

Zapewnia bezpieczne dla typu "opakowanie" dla `CPtrArray` `CObArray`obiektów klasy lub .

## <a name="syntax"></a>Składnia

```
template<class BASE_CLASS, class TYPE>
class CTypedPtrArray : public BASE_CLASS
```

#### <a name="parameters"></a>Parametry

*BASE_CLASS*<br/>
Klasa podstawowa klasy tablicy wskaźnika wpisanego; musi być klasą `CObArray` `CPtrArray`tablicową ( lub ).

*TYP*<br/>
Typ elementów przechowywanych w tablicy klasy podstawowej.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTypedPtrArray::Dodaj](#add)|Dodaje nowy element na końcu tablicy. W razie potrzeby powiększa tablicę|
|[CTypedPtrArray::Dołącz](#append)|Dodaje zawartość jednej tablicy na końcu innej. W razie potrzeby powiększa tablicę|
|[CTypedPtrArray::Kopiowanie](#copy)|Kopiuje inną tablicę do tablicy; w razie potrzeby zwiększa tablicę.|
|[CTypedPtrArray::ElementAt](#elementat)|Zwraca tymczasowe odwołanie do wskaźnika elementu w tablicy.|
|[CTypedPtrArray::GetAt](#getat)|Zwraca wartość w danym indeksie.|
|[CTypedPtrArray::InsertAt](#insertat)|Wstawia element (lub wszystkie elementy w innej tablicy) w określonym indeksie.|
|[CTypedPtrArray::SetAt](#setat)|Ustawia wartość dla danego indeksu; tablicy nie może rosnąć.|
|[CTypedPtrArray::SetAtGrow](#setatgrow)|Ustawia wartość dla danego indeksu; w razie potrzeby zwiększa tablicę.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTypedPtrArray::operator \[\]](#operator_at)|Ustawia lub pobiera element w określonym indeksie.|

## <a name="remarks"></a>Uwagi

Podczas korzystania, `CTypedPtrArray` `CPtrArray` a `CObArray`nie lub , C++ funkcji sprawdzania typu pomaga wyeliminować błędy spowodowane przez niedopasowane typy wskaźników.

Ponadto `CTypedPtrArray` otoka wykonuje większość odlewania, które byłyby wymagane, jeśli używany `CObArray` lub `CPtrArray`.

Ponieważ `CTypedPtrArray` wszystkie funkcje są wbudowane, użycie tego szablonu nie ma znaczącego wpływu na rozmiar lub szybkość kodu.

Aby uzyskać więcej `CTypedPtrArray`informacji na temat używania , zobacz artykuły [Kolekcje](../../mfc/collections.md) i [klasy oparte na szablonach](../../mfc/template-based-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`BASE_CLASS`

`CTypedPtrArray`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtempl.h

## <a name="ctypedptrarrayadd"></a><a name="add"></a>CTypedPtrArray::Dodaj

Ta funkcja `BASE_CLASS`elementu członkowskiego wywołuje **::Add**.

```
INT_PTR Add(TYPE newElement);
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementu, który ma zostać dodany do tablicy.

*nowyElement*<br/>
Element, który ma zostać dodany do tej tablicy.

### <a name="return-value"></a>Wartość zwracana

Indeks dodanego elementu.

### <a name="remarks"></a>Uwagi

Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObArray::Add](../../mfc/reference/cobarray-class.md#add).

## <a name="ctypedptrarrayappend"></a><a name="append"></a>CTypedPtrArray::Dołącz

Ta funkcja `BASE_CLASS`elementu członkowskiego wywołuje ::Append**.

```
INT_PTR Append(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>Parametry

*BASE_CLASS*<br/>
Klasa podstawowa klasy tablicy wskaźnika wpisanego; musi być klasą tablicową ( [CObArray](../../mfc/reference/cobarray-class.md) lub [CPtrArray](../../mfc/reference/cptrarray-class.md)).

*TYP*<br/>
Typ elementów przechowywanych w tablicy klasy podstawowej.

*src*<br/>
Źródło elementów, które mają być dołączone do tablicy.

### <a name="return-value"></a>Wartość zwracana

Indeks pierwszego dołączonego elementu.

### <a name="remarks"></a>Uwagi

Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObArray::Dołącz](../../mfc/reference/cobarray-class.md#append).

## <a name="ctypedptrarraycopy"></a><a name="copy"></a>CTypedPtrArray::Kopiowanie

Ta funkcja `BASE_CLASS`elementu członkowskiego wywołuje **::Copy**.

```cpp
void Copy(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>Parametry

*BASE_CLASS*<br/>
Klasa podstawowa klasy tablicy wskaźnika wpisanego; musi być klasą tablicową ( [CObArray](../../mfc/reference/cobarray-class.md) lub [CPtrArray](../../mfc/reference/cptrarray-class.md)).

*TYP*<br/>
Typ elementów przechowywanych w tablicy klasy podstawowej.

*src*<br/>
Źródło elementów, które mają zostać skopiowane do tablicy.

### <a name="remarks"></a>Uwagi

Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObArray::Copy](../../mfc/reference/cobarray-class.md#copy).

## <a name="ctypedptrarrayelementat"></a><a name="elementat"></a>CTypedPtrArray::ElementAt

Ta wbudowana `BASE_CLASS`funkcja wywołuje **::ElementAt**.

```
TYPE& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów przechowywanych w tej tablicy.

*Nindex*<br/>
Indeks liczby całkowitej, który jest większy lub równy 0 i `BASE_CLASS`mniejszy lub równy wartości zwracanej przez **::GetUpperBound**.

### <a name="return-value"></a>Wartość zwracana

Tymczasowe odwołanie do elementu w lokalizacji określonej przez *nIndex*. Ten element jest typem określonym przez parametr szablonu *TYP*.

### <a name="remarks"></a>Uwagi

Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat).

## <a name="ctypedptrarraygetat"></a><a name="getat"></a>CTypedPtrArray::GetAt

Ta wbudowana `BASE_CLASS`funkcja wywołuje **::GetAt**.

```
TYPE GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów przechowywanych w tablicy.

*Nindex*<br/>
Indeks liczby całkowitej, który jest większy lub równy 0 i `BASE_CLASS`mniejszy lub równy wartości zwracanej przez **::GetUpperBound**.

### <a name="return-value"></a>Wartość zwracana

Kopia elementu w lokalizacji określonej przez *nIndex*. Ten element jest typem określonym przez parametr szablonu *TYP*.

### <a name="remarks"></a>Uwagi

Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)

## <a name="ctypedptrarrayinsertat"></a><a name="insertat"></a>CTypedPtrArray::InsertAt

Ta funkcja `BASE_CLASS`elementu członkowskiego wywołuje **::InsertAt**.

```cpp
void InsertAt(
    INT_PTR nIndex,
    TYPE newElement,
    INT_PTR nCount = 1);

void InsertAt(
    INT_PTR nStartIndex,
    CTypedPtrArray<BASE_CLASS, TYPE>* pNewArray);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks liczby całkowitej, który może być większy niż wartość zwrócona przez [CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound).

*TYP*<br/>
Typ elementów przechowywanych w tablicy klasy podstawowej.

*nowyElement*<br/>
Wskaźnik obiektu, który ma zostać umieszczony w tej tablicy. *NewElement* wartości **NULL** jest dozwolone.

*Ncount*<br/>
Liczba wstawienia tego elementu (wartość domyślna to 1).

*nStartIndex*<br/>
Indeks liczby całkowitej, który może być `CObArray::GetUpperBound`większy niż wartość zwracana przez .

*BASE_CLASS*<br/>
Klasa podstawowa klasy tablicy wskaźnika wpisanego; musi być klasą tablicową ( [CObArray](../../mfc/reference/cobarray-class.md) lub [CPtrArray](../../mfc/reference/cptrarray-class.md)).

*pNewArray (Nienawisłość)*<br/>
Inna tablica, która zawiera elementy, które mają zostać dodane do tej tablicy.

### <a name="remarks"></a>Uwagi

Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat).

## <a name="ctypedptrarrayoperator--"></a><a name="operator_at"></a>CTypedPtrArray::operator [ ]

Te operatory `BASE_CLASS`wbudowane **wywołać ::operator [ ]**.

```
TYPE& operator[ ](int_ptr nindex);
TYPE operator[ ](int_ptr nindex) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów przechowywanych w tablicy.

*Nindex*<br/>
Indeks liczby całkowitej, który jest większy lub równy 0 i `BASE_CLASS`mniejszy lub równy wartości zwracanej przez **::GetUpperBound**.

### <a name="remarks"></a>Uwagi

Pierwszy operator, wywoływany dla tablic, które nie są **const**, może być używany po prawej stronie (r-value) lub po lewej stronie (l-value) instrukcji przypisania. Drugi, wywoływany dla tablic **const,** może być używany tylko po prawej stronie.

Wersja debugowania biblioteki potwierdza, jeśli indeks dolny (po lewej lub prawej stronie instrukcji przypisania) jest poza granicami.

## <a name="ctypedptrarraysetat"></a><a name="setat"></a>CTypedPtrArray::SetAt

Ta funkcja `BASE_CLASS`elementu członkowskiego wywołuje **::SetAt**.

```cpp
void SetAt(
    INT_PTR nIndex,
    TYPE ptr);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks liczby całkowitej, który jest większy lub równy 0 i mniejszy lub równy wartości zwróconej przez [CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound).

*TYP*<br/>
Typ elementów przechowywanych w tablicy klasy podstawowej.

*Ptr*<br/>
Wskaźnik do elementu, który ma zostać wstawiony do tablicy w nIndex. Wartość NULL jest dozwolona.

### <a name="remarks"></a>Uwagi

Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat).

## <a name="ctypedptrarraysetatgrow"></a><a name="setatgrow"></a>CTypedPtrArray::SetAtGrow

Ta funkcja `BASE_CLASS`elementu członkowskiego wywołuje **::SetAtGrow**.

```cpp
void SetAtGrow(
    INT_PTR nIndex,
    TYPE newElement);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks liczby całkowitej, który jest większy lub równy 0.

*TYP*<br/>
Typ elementów przechowywanych w tablicy klasy podstawowej.

*nowyElement*<br/>
Wskaźnik obiektu, który ma zostać dodany do tej tablicy. Wartość **NULL** jest dozwolona.

### <a name="remarks"></a>Uwagi

Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow).

## <a name="see-also"></a>Zobacz też

[MFC Próbki COLLECT](../../overview/visual-cpp-samples.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CPtrArray](../../mfc/reference/cptrarray-class.md)<br/>
[Klasa CObArray](../../mfc/reference/cobarray-class.md)
