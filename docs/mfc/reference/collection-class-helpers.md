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
ms.openlocfilehash: 05fe49a4d8e6de92c584d40f3871f3efb906c7c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374812"
---
# <a name="collection-class-helpers"></a>Pomocnicy klasy kolekcji

Klasy `CMap`kolekcji `CList`i `CArray` użyj szablonu globalnych funkcji pomocnika do takich celów, jak porównywanie, kopiowanie i serialowanie elementów. W ramach implementacji klas `CMap`opartych na `CList`programie , i `CArray`, należy zastąpić te funkcje w razie potrzeby wersjami dostosowanymi do typu danych przechowywanych na mapie, liście lub tablicy. Aby uzyskać informacje na temat zastępowania funkcji pomocnika, takich jak `SerializeElements`, zobacz artykuł [Kolekcje: Jak zrobić kolekcję bezpieczną](../../mfc/how-to-make-a-type-safe-collection.md)dla typu . Należy `ConstructElements` zauważyć, że i `DestructElements` zostały przestarzałe.

Biblioteka klas Programu Microsoft Foundation udostępnia następujące funkcje globalne w pliku afxtempl.h ułatwiające dostosowywanie klas kolekcji:

### <a name="collection-class-helpers"></a>Pomocnicy klasy kolekcji

|||
|-|-|
|[Porównajelementy](#compareelements)|Wskazuje, czy elementy są takie same.|
|[CopyElements (Kopiowanieelementy)](#copyelements)|Kopiuje elementy z jednej tablicy do drugiej.|
|[DumpElements (DumpElements)](#dumpelements)|Zapewnia wyjście diagnostyczne zorientowane na strumień.|
|[Klawisz hashKey](#hashkey)|Oblicza klucz skrótu.|
|[SerializeElements](#serializeelements)|Przechowuje lub pobiera elementy do lub z archiwum.|

## <a name="compareelements"></a><a name="compareelements"></a>Porównajelementy

Wywoływane bezpośrednio przez [CList::Find](clist-class.md#not_found.md#clist__find i pośrednio przez [cmap__lookup](cmap-class.md#lookup) i [cmap__operator &#91;&#93;](cmap-class.md#operator_at).

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
Wskaźnik do pierwszego elementu do porównania.

*ARG_TYPE*<br/>
Typ drugiego elementu, który ma zostać porównany.

*pElement2*<br/>
Wskaźnik do drugiego elementu do porównania.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli obiekt wskazywalny przez *pElement1* jest równy obiektowi wskazywowi przez *pElement2;* w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`CMap` Wywołania używają `CMap` parametrów szablonu *KEY* i *ARG_KEY*.

Domyślna implementacja zwraca wynik porównania * \*pElement1* i * \*pElement2*. Zastądeń tę funkcję, tak aby porównuje elementy w sposób, który jest odpowiedni dla aplikacji.

Język C++ definiuje operator porównania `==`( ) dla typów prostych **(char**, **int**, **float**i tak dalej), ale nie definiuje operatora porównania dla klas i struktur. Jeśli chcesz użyć `CompareElements` lub utworzyć wystąpienia jednej z klas kolekcji, która go używa, należy `CompareElements` zdefiniować operator porównania lub przeciążenie z wersją, która zwraca odpowiednie wartości.

### <a name="requirements"></a>Wymagania

   **Nagłówek:** afxtempl.h

## <a name="copyelements"></a><a name="copyelements"></a>CopyElements (Kopiowanieelementy)

Ta funkcja jest wywoływana bezpośrednio przez [CArray::Dołącz](carray-class.md#append) i [CArray::Copy](carray-class.md#copy).

```
template<class TYPE>
void AFXAPI CopyElements(
    TYPE* pDest,
    const TYPE* pSrc,
    INT_PTR nCount);
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów do skopiowania.

*pDest (właśc.*<br/>
Wskaźnik do miejsca docelowego, w którym elementy zostaną skopiowane.

*Psrc*<br/>
Wskaźnik do źródła elementów, które mają zostać skopiowane.

*Ncount*<br/>
Liczba elementów do skopiowania.

### <a name="remarks"></a>Uwagi

Domyślna implementacja używa prostego **=** operatora przypisania ( ) do wykonania operacji kopiowania. Jeśli typ kopiowany nie ma przeciążony operator =, a następnie domyślnej implementacji wykonuje bitową kopię.

Aby uzyskać informacje na temat implementowania tej i innych funkcji pomocnika, zobacz artykuł [Kolekcje: Jak zrobić kolekcję bezpieczną](../how-to-make-a-type-safe-collection.md)dla typu .

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxtempl.h

## <a name="dumpelements"></a><a name="dumpelements"></a>DumpElements (DumpElements)

Zapewnia dane wyjściowe diagnostyczne zorientowane na strumień w postaci tekstowej dla elementów kolekcji po zastąpieniu.

```
template<class TYPE>
void  AFXAPI DumpElements(
    CDumpContext& dc,
    const TYPE* pElements,
    INT_PTR nCount);
```

### <a name="parameters"></a>Parametry

*Dc*<br/>
Kontekst zrzutu dla elementów dumpingu.

*TYP*<br/>
Parametr szablonu określający typ elementów.

*pElementy*<br/>
Wskaźnik do elementów, które mają być po cenach dumpingowych.

*Ncount*<br/>
Liczba elementów, które mają być po cenach dumpingowych.

### <a name="remarks"></a>Uwagi

Funkcja `CArray::Dump` `CList::Dump`, `CMap::Dump` i funkcje wywołają to, jeśli głębokość zrzutu jest większa niż 0.

Domyślna implementacja nic nie robi. Jeśli elementy kolekcji pochodzą z `CObject`, zastąpienie zazwyczaj iteracji za pośrednictwem kolekcji elementów, wzywając `Dump` do każdego elementu po kolei.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxtempl.h

## <a name="hashkey"></a><a name="hashkey"></a>Klawisz hashKey

Oblicza wartość mieszania dla danego klucza.

```
template<class ARG_KEY>
AFX_INLINE UINT AFXAPI HashKey(ARG_KEY  key);
```

### <a name="parameters"></a>Parametry

*ARG_KEY*<br/>
Parametr szablonu określający typ danych używany do uzyskiwania dostępu do kluczy mapy.

*key*<br/>
Klucz, którego wartość mieszania ma być obliczona.

### <a name="return-value"></a>Wartość zwracana

Wartość skrótu klucza.

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana bezpośrednio przez [CMap::RemoveKey](cmap-class.md#removekey) i pośrednio przez [CMap::Lookup](cmap-class.md#lookup) i [CMap::Operator &#91;&#93;](cmap-class.md#operator_at).

Domyślna implementacja tworzy wartość mieszania przez przesunięcie *klucza* w prawo o cztery pozycje. Zastądeń tę funkcję, tak aby zwracała wartości skrótu odpowiednie dla aplikacji.

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

  **Nagłówek** afxtempl.h

## <a name="serializeelements"></a><a name="serializeelements"></a>SerializeElements

[CArray](carray-class.md), [CList](clist-class.md)i [CMap](cmap-class.md) wywołać tę funkcję do serializacji elementów.

```
template<class TYPE>
void AFXAPI SerializeElements(CArchive& ar, TYPE* pElements, INT_PTR nCount);
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów.

*Ar*<br/>
Obiekt archiwum do archiwizacji do lub z.

*pElementy*<br/>
Wskaźnik do elementów, które są archiwizowane.

*Ncount*<br/>
Liczba elementów archiwizowanych

### <a name="remarks"></a>Uwagi

Domyślna implementacja wykonuje bitowy odczyt lub zapis.

Aby uzyskać informacje na temat implementowania tej i innych funkcji pomocnika, zobacz artykuł [Kolekcje: Jak zrobić kolekcję bezpieczną](../how-to-make-a-type-safe-collection.md)dla typu .

### <a name="example"></a>Przykład

Zobacz przykład w [artykule Kolekcje: Jak zrobić kolekcję bezpieczną](../how-to-make-a-type-safe-collection.md)dla typu .

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxtempl.h

## <a name="see-also"></a>Zobacz też

[Makra i globals](mfc-macros-and-globals.md)<br/>
[Klasa CMap](cmap-class.md)<br/>
[Klasa CList](clist-class.md)<br/>
[Klasa CArray](carray-class.md)
