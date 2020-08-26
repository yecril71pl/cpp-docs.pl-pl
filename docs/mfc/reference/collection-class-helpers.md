---
title: Pomocnicy klasy kolekcji
ms.date: 11/04/2016
helpviewer_keywords:
- DestructElements function
- ConstructElements function
- SerializeElements function
- collection classes [MFC], helper functions
- helper functions collection class [MFC]
ms.assetid: bc3a2368-9edd-4748-9e6a-13cba79517ca
ms.openlocfilehash: 04b142cde12a9795f217559f875eef7fcec3b0f2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841431"
---
# <a name="collection-class-helpers"></a>Pomocnicy klasy kolekcji

Klasy kolekcji, `CMap` `CList` i `CArray` używają globalnych funkcji pomocników z szablonami do takich celów jak porównywanie, kopiowanie i Serializowanie elementów. W ramach implementacji klas opartych na `CMap` , `CList` , i `CArray` , należy przesłonić te funkcje w miarę potrzeb z wersjami dostosowany do typu danych przechowywanych na mapie, liście lub tablicy. Aby uzyskać informacje na temat zastępowania funkcji pomocnika, takich jak `SerializeElements` , zobacz [kolekcje artykułów: jak utworzyć bezpieczną metodę zbierania danych](../../mfc/how-to-make-a-type-safe-collection.md). Należy pamiętać, że `ConstructElements` `DestructElements` są one przestarzałe.

Biblioteka MFC udostępnia następujące funkcje globalne w afxtempl. h, które ułatwiają Dostosowywanie klas kolekcji:

### <a name="collection-class-helpers"></a>Pomocnicy klasy kolekcji

|Nazwa|Opis|
|-|-|
|[CompareElements](#compareelements)|Wskazuje, czy elementy są takie same.|
|[CopyElements](#copyelements)|Kopiuje elementy z jednej tablicy do innej.|
|[DumpElements](#dumpelements)|Zapewnia zorientowane na strumień dane wyjściowe diagnostyki.|
|[HashKey](#hashkey)|Oblicza klucz skrótu.|
|[SerializeElements](#serializeelements)|Przechowuje lub Pobiera elementy do archiwum lub z niego.|

## <a name="compareelements"></a><a name="compareelements"></a> CompareElements

Wywoływana bezpośrednio przez [CList:: find] (CList-Class. MD # not_found. MD # clist__find i pośrednio przez [cmap__lookup](cmap-class.md#lookup) i [cmap__operator &#91;&#93;](cmap-class.md#operator_at).

```
template<class TYPE, class ARG_TYPE>
BOOL AFXAPI
CompareElements(
    const TYPE* pElement1,
    const ARG_TYPE* pElement2);
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Typ pierwszego elementu, który ma zostać porównany.

*pElement1*<br/>
Wskaźnik do pierwszego elementu, który ma zostać porównany.

*ARG_TYPE*<br/>
Typ drugiego elementu, który ma zostać porównany.

*pElement2*<br/>
Wskaźnik do drugiego elementu, który ma zostać porównany.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli obiekt wskazany przez *pElement1* jest równy obiektowi wskazywanym przez *pElement2*; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`CMap`Wywołania używają `CMap` *klucza* parametrów szablonu i *ARG_KEY*.

Domyślna implementacja zwraca wynik porównania * \* pElement1* i * \* pElement2*. Zastąp tę funkcję, aby porównuje elementy w sposób odpowiedni dla Twojej aplikacji.

Język C++ definiuje operator porównania ( `==` ) dla typów prostych ( **`char`** ,,, **`int`** itd **`float`** .), ale nie definiuje operatora porównania dla klas i struktur. Jeśli chcesz użyć `CompareElements` lub aby utworzyć wystąpienie jednej z klas kolekcji, która używa tego elementu, musisz zdefiniować operator porównania lub Przeciążenie `CompareElements` z wersją, która zwraca odpowiednie wartości.

### <a name="requirements"></a>Wymagania

   **Nagłówek:** afxtempl. h

## <a name="copyelements"></a><a name="copyelements"></a> CopyElements

Ta funkcja jest wywoływana bezpośrednio przez [CArray:: Append](carray-class.md#append) i [CArray:: Copy](carray-class.md#copy).

```
template<class TYPE>
void AFXAPI CopyElements(
    TYPE* pDest,
    const TYPE* pSrc,
    INT_PTR nCount);
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów, które mają zostać skopiowane.

*pDest*<br/>
Wskaźnik do miejsca docelowego, do którego zostaną skopiowane elementy.

*pSrc*<br/>
Wskaźnik do źródła elementów, które mają zostać skopiowane.

*nCount*<br/>
Liczba elementów, które mają zostać skopiowane.

### <a name="remarks"></a>Uwagi

Implementacja domyślna używa prostego operatora przypisania ( **=** ) do wykonania operacji kopiowania. Jeśli kopiowany typ nie ma przeciążonego operatora =, to domyślna implementacja wykonuje kopię bitową.

Aby uzyskać informacje na temat wdrażania tej i innych funkcji pomocnika, zobacz [kolekcje artykułów: jak utworzyć bezpieczną metodę zbierania danych](../how-to-make-a-type-safe-collection.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxtempl. h

## <a name="dumpelements"></a><a name="dumpelements"></a> DumpElements

Zapewnia zorientowane na strumień dane wyjściowe diagnostyki w postaci tekstowej dla elementów kolekcji, gdy jest zastępowany.

```
template<class TYPE>
void  AFXAPI DumpElements(
    CDumpContext& dc,
    const TYPE* pElements,
    INT_PTR nCount);
```

### <a name="parameters"></a>Parametry

*DC*<br/>
Kontekst zrzutu dla elementów zrzucających.

*TYP*<br/>
Parametr szablonu określający typ elementów.

*pElements*<br/>
Wskaźnik na elementy, które mają zostać poddane zrzutu.

*nCount*<br/>
Liczba elementów, które mają zostać poddane zrzutu.

### <a name="remarks"></a>Uwagi

`CArray::Dump`Funkcje, `CList::Dump` i `CMap::Dump` wywołują tę funkcję, jeśli głębokość zrzutu jest większa niż 0.

Domyślna implementacja nie robi nic. Jeśli elementy kolekcji pochodzą z `CObject` , przesłonięcie zwykle przejdzie przez elementy kolekcji, wywołując `Dump` dla każdego elementu z kolei.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxtempl. h

## <a name="hashkey"></a><a name="hashkey"></a> HashKey

Oblicza wartość skrótu dla danego klucza.

```
template<class ARG_KEY>
AFX_INLINE UINT AFXAPI HashKey(ARG_KEY  key);
```

### <a name="parameters"></a>Parametry

*ARG_KEY*<br/>
Parametr szablonu określający typ danych służący do uzyskiwania dostępu do kluczy mapowania.

*głównych*<br/>
Klucz, dla którego ma zostać obliczona wartość skrótu.

### <a name="return-value"></a>Wartość zwracana

Wartość skrótu klucza.

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana bezpośrednio przez [CMAP:: RemoveKey](cmap-class.md#removekey) i pośrednio przez [CMAP:: Lookup](cmap-class.md#lookup) i [CMAP:: operator &#91;&#93;](cmap-class.md#operator_at).

Domyślna implementacja powoduje utworzenie wartości skrótu przez przesunięcie *klucza* w prawo przez cztery pozycje. Przesłoń tę funkcję, aby zwracała wartości skrótu odpowiednie dla aplikacji.

### <a name="example"></a>Przykład

```cpp
template <> UINT AFXAPI HashKey(unsigned __int64 key)
{
   // Generate the hash value by XORing the lower 32 bits of the number
   // with the upper 32 bits
   return(UINT(key) ^ UINT(key >> 32));
}
```

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxtempl. h

## <a name="serializeelements"></a><a name="serializeelements"></a> SerializeElements

[CArray](carray-class.md), [CList](clist-class.md)i [CMAP](cmap-class.md) Wywołaj tę funkcję, aby serializować elementy.

```
template<class TYPE>
void AFXAPI SerializeElements(CArchive& ar, TYPE* pElements, INT_PTR nCount);
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów.

*ty*<br/>
Obiekt archiwum do archiwizacji lub z.

*pElements*<br/>
Wskaźnik do elementów, które są archiwizowane.

*nCount*<br/>
Liczba archiwizowanych elementów

### <a name="remarks"></a>Uwagi

Domyślna implementacja to bitowy odczyt lub zapis.

Aby uzyskać informacje na temat wdrażania tej i innych funkcji pomocnika, zobacz [kolekcje artykułów: jak utworzyć bezpieczną metodę zbierania danych](../how-to-make-a-type-safe-collection.md).

### <a name="example"></a>Przykład

Zapoznaj się z przykładem w artykule [kolekcje artykułów: jak utworzyć bezpieczną metodę zbierania danych](../how-to-make-a-type-safe-collection.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxtempl. h

## <a name="see-also"></a>Zobacz też

[Makra i Globals](mfc-macros-and-globals.md)<br/>
[Klasa CMap](cmap-class.md)<br/>
[Klasa CList](clist-class.md)<br/>
[Klasa CArray](carray-class.md)
