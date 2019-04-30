---
title: Ctypedptrarray — klasa
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
ms.openlocfilehash: 080e47746b83b6ff12db9f6df0fc27bcd202bb51
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346087"
---
# <a name="ctypedptrarray-class"></a>Ctypedptrarray — klasa

Oferuje bezpieczne "opakowanie" dla obiektów klasy `CPtrArray` lub `CObArray`.

## <a name="syntax"></a>Składnia

```
template<class BASE_CLASS, class TYPE>
class CTypedPtrArray : public BASE_CLASS
```

#### <a name="parameters"></a>Parametry

*BASE_CLASS*<br/>
Klasą bazową klasy tablicy wpisane wskaźnika; musi być array — klasa ( `CObArray` lub `CPtrArray`).

*TYP*<br/>
Typ elementów przechowywanych w tablicy klasy bazowej.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTypedPtrArray::Add](#add)|Dodaje nowy element do końca tablicy. Powiększa się tablica, jeśli to konieczne|
|[CTypedPtrArray::Append](#append)|Dodaje zawartość jednej tablicy do końca innej. Powiększa się tablica, jeśli to konieczne|
|[CTypedPtrArray::Copy](#copy)|Kopiuje innej tablicy do tablicy; zwiększa rozmiar tablicy, jeśli to konieczne.|
|[CTypedPtrArray::ElementAt](#elementat)|Zwraca tymczasowe odwołanie do wskaźnika elementu w tablicy.|
|[CTypedPtrArray::GetAt](#getat)|Zwraca wartość pod danym indeksem.|
|[CTypedPtrArray::InsertAt](#insertat)|Wstawia element (lub wszystkie elementy w innej tablicy) z określonym indeksem.|
|[CTypedPtrArray::SetAt](#setat)|Ustawia wartość dla podanego indeksu; Tablica nie może wzrosnąć.|
|[CTypedPtrArray::SetAtGrow](#setatgrow)|Ustawia wartość dla podanego indeksu; zwiększa rozmiar tablicy, jeśli to konieczne.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTypedPtrArray::operator \[ \]](#operator_at)|Ustawia lub pobiera element pod określonym indeksem.|

## <a name="remarks"></a>Uwagi

Kiedy używasz `CTypedPtrArray` zamiast `CPtrArray` lub `CObArray`, funkcji Kontrola typów w języku C++, pomaga wyeliminować sytuację błędów spowodowanych przez wskaźnik niezgodne typy.

Ponadto `CTypedPtrArray` otoki wykonuje większość rzutowania, które będą wymagane, jeśli użyto `CObArray` lub `CPtrArray`.

Ponieważ wszystkie `CTypedPtrArray` funkcje są wbudowane, użyj tego szablonu nie znacząco wpływa na rozmiar lub prędkość kodu.

Aby uzyskać więcej informacji na temat korzystania z `CTypedPtrArray`, zobacz artykuły [kolekcje](../../mfc/collections.md) i [oparte na szablonach klas](../../mfc/template-based-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`BASE_CLASS`

`CTypedPtrArray`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtempl.h

##  <a name="add"></a>  CTypedPtrArray::Add

Ta funkcja elementu członkowskiego wywołuje `BASE_CLASS` **:: Dodaj**.

```
INT_PTR Add(TYPE newElement);
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementu do dodania do tablicy.

*newElement*<br/>
Element, który ma zostać dodany do tej tablicy.

### <a name="return-value"></a>Wartość zwracana

Indeks dodanego elementu.

### <a name="remarks"></a>Uwagi

Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObArray::Add](../../mfc/reference/cobarray-class.md#add).

##  <a name="append"></a>  CTypedPtrArray::Append

Ta funkcja elementu członkowskiego wywołuje `BASE_CLASS`:: Dołącz **.

```
INT_PTR Append(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>Parametry

*BASE_CLASS*<br/>
Klasą bazową klasy tablicy wpisane wskaźnika; musi być array — klasa ( [CObArray](../../mfc/reference/cobarray-class.md) lub [CPtrArray](../../mfc/reference/cptrarray-class.md)).

*TYP*<br/>
Typ elementów przechowywanych w tablicy klasy bazowej.

*src*<br/>
Źródło elementów, które mają być dołączane do tablicy.

### <a name="return-value"></a>Wartość zwracana

Indeks pierwszy dołączony element.

### <a name="remarks"></a>Uwagi

Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObArray::Append](../../mfc/reference/cobarray-class.md#append).

##  <a name="copy"></a>  CTypedPtrArray::Copy

Ta funkcja elementu członkowskiego wywołuje `BASE_CLASS` **:: kopiowania**.

```
void Copy(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>Parametry

*BASE_CLASS*<br/>
Klasą bazową klasy tablicy wpisane wskaźnika; musi być array — klasa ( [CObArray](../../mfc/reference/cobarray-class.md) lub [CPtrArray](../../mfc/reference/cptrarray-class.md)).

*TYP*<br/>
Typ elementów przechowywanych w tablicy klasy bazowej.

*src*<br/>
Źródło elementów, które mają być kopiowane do tablicy.

### <a name="remarks"></a>Uwagi

Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObArray::Copy](../../mfc/reference/cobarray-class.md#copy).

##  <a name="elementat"></a>  CTypedPtrArray::ElementAt

Ta funkcja śródwierszowa wywołuje `BASE_CLASS` **:: ElementAt**.

```
TYPE& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów przechowywanych w tej tablicy.

*nIndex*<br/>
Liczba całkowita indeksu, który jest większa lub równa 0 i mniejsza niż wartość zwrócona przez obiekt `BASE_CLASS` **:: GetUpperBound**.

### <a name="return-value"></a>Wartość zwracana

Tymczasowe odwołanie do elementu w lokalizacji określonej przez *nIndex*. Ten element jest typu określonego przez parametr szablonu *typu*.

### <a name="remarks"></a>Uwagi

Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat).

##  <a name="getat"></a>  CTypedPtrArray::GetAt

Ta funkcja śródwierszowa wywołuje `BASE_CLASS` **:: GetAt**.

```
TYPE GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów przechowywanych w tablicy.

*nIndex*<br/>
Liczba całkowita indeksu, który jest większa lub równa 0 i mniejsza niż wartość zwrócona przez obiekt `BASE_CLASS` **:: GetUpperBound**.

### <a name="return-value"></a>Wartość zwracana

Kopia elementu w lokalizacji określonej przez *nIndex*. Ten element jest typu określonego przez parametr szablonu *typu*.

### <a name="remarks"></a>Uwagi

Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)

##  <a name="insertat"></a>  CTypedPtrArray::InsertAt

Ta funkcja elementu członkowskiego wywołuje `BASE_CLASS` **:: InsertAt**.

```
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
Liczba całkowita indeksu, który może być większa niż wartość zwrócona przez obiekt [CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound).

*TYP*<br/>
Typ elementów przechowywanych w tablicy klasy bazowej.

*newElement*<br/>
Wskaźnik obiektu można umieścić w tej tablicy. A *newElement* wartości **NULL** jest dozwolone.

*nCount*<br/>
Liczba przypadków, gdy ten element powinien być wstawiany (wartość domyślna to 1).

*nStartIndex*<br/>
Liczba całkowita indeksu, który może być większa niż wartość zwrócona przez obiekt `CObArray::GetUpperBound`.

*BASE_CLASS*<br/>
Klasą bazową klasy tablicy wpisane wskaźnika; musi być array — klasa ( [CObArray](../../mfc/reference/cobarray-class.md) lub [CPtrArray](../../mfc/reference/cptrarray-class.md)).

*pNewArray*<br/>
Innej tablicy, która zawiera elementy, które mają zostać dodane do tej tablicy.

### <a name="remarks"></a>Uwagi

Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat).

##  <a name="operator_at"></a>  [] CTypedPtrArray::operator

Te operatory tekście wywołania `BASE_CLASS` **:: operator []**.

```
TYPE& operator[ ](int_ptr nindex);
TYPE operator[ ](int_ptr nindex) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów przechowywanych w tablicy.

*nIndex*<br/>
Liczba całkowita indeksu, który jest większa lub równa 0 i mniejsza niż wartość zwrócona przez obiekt `BASE_CLASS` **:: GetUpperBound**.

### <a name="remarks"></a>Uwagi

Pierwszy operator wywoływane dla tablic, które nie są **const**, mogą być używane w prawo (r) lub po lewej stronie (l wartość) instrukcji przypisania. Druga Strona, wywołany dla **const** tablic, mogą służyć tylko po prawej stronie.

Wersja do debugowania biblioteki potwierdza, jeśli indeksu dolnego (albo po lewej lub prawej stronie instrukcji przypisania) jest poza zakresem.

##  <a name="setat"></a>  CTypedPtrArray::SetAt

Ta funkcja elementu członkowskiego wywołuje `BASE_CLASS` **:: SetAt**.

```
void SetAt(
    INT_PTR nIndex,
    TYPE ptr);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Liczba całkowita indeksu, który jest większa lub równa 0 i mniejsza niż wartość zwrócona przez obiekt [CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound).

*TYP*<br/>
Typ elementów przechowywanych w tablicy klasy bazowej.

*ptr*<br/>
Wskaźnik do elementu, który ma zostać wstawiony w tablicy, od nIndex. Wartość NULL jest dozwolona.

### <a name="remarks"></a>Uwagi

Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat).

##  <a name="setatgrow"></a>  CTypedPtrArray::SetAtGrow

Ta funkcja elementu członkowskiego wywołuje `BASE_CLASS` **:: SetAtGrow**.

```
void SetAtGrow(
    INT_PTR nIndex,
    TYPE newElement);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks liczby całkowitej, która jest większa lub równa 0.

*TYP*<br/>
Typ elementów przechowywanych w tablicy klasy bazowej.

*newElement*<br/>
Obiekt wskaźnika, który ma zostać dodany do tej tablicy. A **NULL** może mieć wartości.

### <a name="remarks"></a>Uwagi

Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow).

## <a name="see-also"></a>Zobacz także

[Próbki MFC ZBIERANIE](../../overview/visual-cpp-samples.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CPtrArray](../../mfc/reference/cptrarray-class.md)<br/>
[Klasa CObArray](../../mfc/reference/cobarray-class.md)
