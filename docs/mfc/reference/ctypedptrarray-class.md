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
ms.openlocfilehash: db24e3992e5db70895ccc2908dba108de843bcdc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215949"
---
# <a name="ctypedptrarray-class"></a>Klasa CTypedPtrArray

Zapewnia bezpieczną "otokę" dla obiektów klasy `CPtrArray` lub `CObArray` .

## <a name="syntax"></a>Składnia

```
template<class BASE_CLASS, class TYPE>
class CTypedPtrArray : public BASE_CLASS
```

#### <a name="parameters"></a>Parametry

*BASE_CLASS*<br/>
Klasa bazowa klasy Array wskaźnika typu; musi być klasą tablicową ( `CObArray` lub `CPtrArray` ).

*TYP*<br/>
Typ elementów przechowywanych w tablicy klasy podstawowej.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTypedPtrArray:: Add](#add)|Dodaje nowy element na końcu tablicy. Powiększa tablicę w razie potrzeby|
|[CTypedPtrArray:: Append](#append)|Dodaje zawartość jednej tablicy do końca innej. Powiększa tablicę w razie potrzeby|
|[CTypedPtrArray:: Copy](#copy)|Kopiuje kolejną tablicę do tablicy; w razie potrzeby powiększa tablicę.|
|[CTypedPtrArray::ElementAt](#elementat)|Zwraca tymczasowe odwołanie do wskaźnika elementu w tablicy.|
|[CTypedPtrArray::GetAt](#getat)|Zwraca wartość w danym indeksie.|
|[CTypedPtrArray::InsertAt](#insertat)|Wstawia element (lub wszystkie elementy w innej tablicy) o określonym indeksie.|
|[CTypedPtrArray::SetAt](#setat)|Ustawia wartość dla danego indeksu; Tablica nie może być większa.|
|[CTypedPtrArray::SetAtGrow](#setatgrow)|Ustawia wartość dla danego indeksu; w razie potrzeby powiększa tablicę.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTypedPtrArray:: operator \[\]](#operator_at)|Ustawia lub pobiera element pod określonym indeksem.|

## <a name="remarks"></a>Uwagi

Gdy używasz `CTypedPtrArray` , a nie `CPtrArray` lub `CObArray` , funkcja sprawdzania typu C++ pomaga wyeliminować błędy spowodowane niezgodnymi typami wskaźnika.

Ponadto `CTypedPtrArray` otoka wykonuje większość rzutowania, które byłyby wymagane, jeśli użyto `CObArray` lub `CPtrArray` .

Ponieważ wszystkie `CTypedPtrArray` funkcje są wbudowane, użycie tego szablonu nie ma znacząco wpływu na rozmiar lub szybkość kodu.

Aby uzyskać więcej informacji na temat korzystania z programu `CTypedPtrArray` , zobacz [kolekcje](../../mfc/collections.md) artykułów i [klasy oparte na szablonach](../../mfc/template-based-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`BASE_CLASS`

`CTypedPtrArray`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtempl. h

## <a name="ctypedptrarrayadd"></a><a name="add"></a>CTypedPtrArray:: Add

Ta funkcja elementu członkowskiego wywołuje `BASE_CLASS` **:: Add**.

```
INT_PTR Add(TYPE newElement);
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementu, który ma zostać dodany do tablicy.

*newElement*<br/>
Element, który ma zostać dodany do tej tablicy.

### <a name="return-value"></a>Wartość zwracana

Indeks dodanego elementu.

### <a name="remarks"></a>Uwagi

Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObArray:: Add](../../mfc/reference/cobarray-class.md#add).

## <a name="ctypedptrarrayappend"></a><a name="append"></a>CTypedPtrArray:: Append

Ta funkcja elementu członkowskiego wywołuje `BASE_CLASS` :: Append * *.

```
INT_PTR Append(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>Parametry

*BASE_CLASS*<br/>
Klasa bazowa klasy Array wskaźnika typu; musi być klasą tablicową ( [CObArray](../../mfc/reference/cobarray-class.md) lub [CPtrArray](../../mfc/reference/cptrarray-class.md)).

*TYP*<br/>
Typ elementów przechowywanych w tablicy klasy podstawowej.

*src*<br/>
Źródło elementów do dołączenia do tablicy.

### <a name="return-value"></a>Wartość zwracana

Indeks pierwszego dołączonego elementu.

### <a name="remarks"></a>Uwagi

Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObArray:: Append](../../mfc/reference/cobarray-class.md#append).

## <a name="ctypedptrarraycopy"></a><a name="copy"></a>CTypedPtrArray:: Copy

Ta funkcja elementu członkowskiego wywołuje `BASE_CLASS` **:: Copy**.

```cpp
void Copy(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>Parametry

*BASE_CLASS*<br/>
Klasa bazowa klasy Array wskaźnika typu; musi być klasą tablicową ( [CObArray](../../mfc/reference/cobarray-class.md) lub [CPtrArray](../../mfc/reference/cptrarray-class.md)).

*TYP*<br/>
Typ elementów przechowywanych w tablicy klasy podstawowej.

*src*<br/>
Źródło elementów, które mają być skopiowane do tablicy.

### <a name="remarks"></a>Uwagi

Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObArray:: Copy](../../mfc/reference/cobarray-class.md#copy).

## <a name="ctypedptrarrayelementat"></a><a name="elementat"></a>CTypedPtrArray::ElementAt

Ta wbudowana funkcja wywołuje `BASE_CLASS` **:: ElementAt**.

```
TYPE& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów przechowywanych w tej tablicy.

*nIndex*<br/>
Indeks liczby całkowitej, który jest większy lub równy 0 i mniejszy lub równy wartości zwróconej przez `BASE_CLASS` **:: GetUpperBound**.

### <a name="return-value"></a>Wartość zwracana

Tymczasowe odwołanie do elementu w lokalizacji określonej przez *nIndex*. Ten element jest typu określonego przez *Typ*parametru szablonu.

### <a name="remarks"></a>Uwagi

Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObArray:: ElementAt](../../mfc/reference/cobarray-class.md#elementat).

## <a name="ctypedptrarraygetat"></a><a name="getat"></a>CTypedPtrArray::GetAt

Ta wbudowana funkcja wywołuje `BASE_CLASS` **:: GetAt**.

```
TYPE GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów przechowywanych w tablicy.

*nIndex*<br/>
Indeks liczby całkowitej, który jest większy lub równy 0 i mniejszy lub równy wartości zwróconej przez `BASE_CLASS` **:: GetUpperBound**.

### <a name="return-value"></a>Wartość zwracana

Kopia elementu w lokalizacji określonej przez *nIndex*. Ten element jest typu określonego przez *Typ*parametru szablonu.

### <a name="remarks"></a>Uwagi

Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObArray:: GetAt](../../mfc/reference/cobarray-class.md#getat)

## <a name="ctypedptrarrayinsertat"></a><a name="insertat"></a>CTypedPtrArray::InsertAt

Ta funkcja elementu członkowskiego wywołuje `BASE_CLASS` **:: InsertAt**.

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

*nIndex*<br/>
Indeks liczby całkowitej, który może być większy niż wartość zwrócona przez [CObArray:: GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound).

*TYP*<br/>
Typ elementów przechowywanych w tablicy klasy podstawowej.

*newElement*<br/>
Wskaźnik obiektu, który ma zostać umieszczony w tej tablicy. *NewElement* wartości **null** jest dozwolony.

*nCount*<br/>
Liczba przypadków wstawienia tego elementu (wartość domyślna to 1).

*nStartIndex*<br/>
Indeks liczby całkowitej, który może być większy niż wartość zwrócona przez `CObArray::GetUpperBound` .

*BASE_CLASS*<br/>
Klasa bazowa klasy Array wskaźnika typu; musi być klasą tablicową ( [CObArray](../../mfc/reference/cobarray-class.md) lub [CPtrArray](../../mfc/reference/cptrarray-class.md)).

*pNewArray*<br/>
Inna tablica zawierająca elementy, które mają zostać dodane do tej tablicy.

### <a name="remarks"></a>Uwagi

Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObArray:: InsertAt](../../mfc/reference/cobarray-class.md#insertat).

## <a name="ctypedptrarrayoperator--"></a><a name="operator_at"></a>CTypedPtrArray:: operator []

Te operatory wbudowane wywołujące `BASE_CLASS` **:: operator []**.

```
TYPE& operator[ ](int_ptr nindex);
TYPE operator[ ](int_ptr nindex) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów przechowywanych w tablicy.

*nIndex*<br/>
Indeks liczby całkowitej, który jest większy lub równy 0 i mniejszy lub równy wartości zwróconej przez `BASE_CLASS` **:: GetUpperBound**.

### <a name="remarks"></a>Uwagi

Pierwszy operator, wywoływany dla tablic, które nie jest **`const`** , może być używany po prawej stronie (r-Value) lub lewej (l-wartości) instrukcji przypisania. Sekunda, wywołana dla **`const`** tablic, może być używana tylko po prawej stronie.

Wersja debugowania biblioteki potwierdza, czy indeks dolny (w lewej lub prawej stronie instrukcji przypisania) znajduje się poza zakresem.

## <a name="ctypedptrarraysetat"></a><a name="setat"></a>CTypedPtrArray::SetAt

Ta funkcja elementu członkowskiego wywołuje `BASE_CLASS` **:: SetAt**.

```cpp
void SetAt(
    INT_PTR nIndex,
    TYPE ptr);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks liczby całkowitej, który jest większy lub równy 0 i mniejszy lub równy wartości zwróconej przez [CObArray:: GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound).

*TYP*<br/>
Typ elementów przechowywanych w tablicy klasy podstawowej.

*ptr*<br/>
Wskaźnik do elementu, który ma zostać wstawiony do tablicy w nIndex. Dozwolona jest wartość NULL.

### <a name="remarks"></a>Uwagi

Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObArray:: SetAt](../../mfc/reference/cobarray-class.md#setat).

## <a name="ctypedptrarraysetatgrow"></a><a name="setatgrow"></a>CTypedPtrArray::SetAtGrow

Ta funkcja elementu członkowskiego wywołuje `BASE_CLASS` **:: SetAtGrow**.

```cpp
void SetAtGrow(
    INT_PTR nIndex,
    TYPE newElement);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks liczby całkowitej, który jest większy lub równy 0.

*TYP*<br/>
Typ elementów przechowywanych w tablicy klasy podstawowej.

*newElement*<br/>
Wskaźnik obiektu, który ma zostać dodany do tej tablicy. Dozwolona jest wartość **null** .

### <a name="remarks"></a>Uwagi

Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObArray:: SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow).

## <a name="see-also"></a>Zobacz także

[ZBIERANIE próbek MFC](../../overview/visual-cpp-samples.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CPtrArray](../../mfc/reference/cptrarray-class.md)<br/>
[Klasa CObArray](../../mfc/reference/cobarray-class.md)
