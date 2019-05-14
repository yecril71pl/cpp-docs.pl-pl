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
ms.openlocfilehash: 6839427d916068deaf2041dd21a282e0b470f404
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65612263"
---
# <a name="collection-class-helpers"></a>Pomocnicy klasy kolekcji

Klasy kolekcji `CMap`, `CList`, i `CArray` do celów takich jak porównywanie, kopiując i serializacji elementów za pomocą funkcji oparte na szablonach pomocnika globalnego. W ramach implementacji klas na podstawie `CMap`, `CList`, i `CArray`, konieczne jest przesłonięcie tych funkcji, zgodnie z potrzebami z wersjami dostosowane do typu danych przechowywanych w mapie, listy lub tablicy. Instrukcje dotyczące zastępowanie funkcji pomocnika, takich jak `SerializeElements`, zapoznaj się z artykułem [kolekcji: Jak utworzyć kolekcję bezpieczny](../../mfc/how-to-make-a-type-safe-collection.md). Należy pamiętać, że `ConstructElements` i `DestructElements` zostały wycofane.

Biblioteki klas Microsoft Foundation udostępnia następujące funkcje globalne w afxtempl.h do dostosowywania Twoje klasy kolekcji:

### <a name="collection-class-helpers"></a>Pomocnicy klasy kolekcji

|||
|-|-|
|[Compareelements —](#compareelements)|Wskazuje, czy elementy są takie same.|
|[Copyelements —](#copyelements)|Kopiuje elementy z jednej tablicy do innej.|
|[Dumpelements —](#dumpelements)|Udostępnia zorientowane na strumień diagnostyczne dane wyjściowe.|
|[HashKey —](#hashkey)|Oblicza wartość skrótu klucza.|
|[Serializeelements —](#serializeelements)|Zapisywanie i odczytywanie elementów do lub z archiwum.|

##  <a name="compareelements"></a>  Compareelements —

Wywoływana bezpośrednio przez [CList::Find] (clist class.md #not_found.md #clist__find i pośrednio [cmap__lookup](cmap-class.md#lookup) i [cmap__operator &#91; &#93; ](cmap-class.md#operator_at).

```
template<class TYPE, class ARG_TYPE>
BOOL AFXAPI
CompareElements(
    const TYPE* pElement1,
    const ARG_TYPE* pElement2);
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Typ pierwszego elementu, który można porównać.

*pElement1*<br/>
Wskaźnik do pierwszego elementu, który można porównać.

*ARG_TYPE*<br/>
Typ drugiego elementu mają być porównane.

*pElement2*<br/>
Wskaźnik do drugiego elementu mają być porównane.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli obiekt wskazywany przez *pElement1* jest taki sam, jak obiekt wskazywany przez *pElement2*; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`CMap` Wymaga użycia `CMap` parametry szablonu *klucz* i *ARG_KEY*.

Domyślna implementacja zwraca wynik porównania  *\*pElement1* i  *\*pElement2*. Należy przesłonić tę funkcję, dzięki czemu porównuje elementów w sposób, który jest odpowiedni dla aplikacji.

Język C++ definiuje operator porównania ( `==`) dla typów prostych (**char**, **int**, **float**i tak dalej), ale nie definiuje operator porównania klasy i struktury. Jeśli chcesz używać `CompareElements` lub do utworzenia wystąpienia jednej z klas kolekcji, które korzysta z niego, należy zdefiniować operator porównania lub przeciążenia `CompareElements` wersją, która zwraca odpowiednie wartości.

### <a name="requirements"></a>Wymagania

   **Nagłówek:** afxtempl.h

##  <a name="copyelements"></a>  Copyelements —

Ta funkcja jest wywoływana bezpośrednio przez [CArray::Append](carray-class.md#append) i [CArray::Copy](carray-class.md#copy).

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
Wskaźnik do miejsca docelowego, do której zostaną skopiowane elementy.

*pSrc*<br/>
Wskaźnik do źródła elementów do skopiowania.

*nCount*<br/>
Liczba elementów do skopiowania.

### <a name="remarks"></a>Uwagi

Domyślna implementacja używa prosty operator przypisania ( **=** ) do wykonania tej operacji kopiowania. Jeśli typ kopiowane nie jest przeciążony operator =, to domyślna implementacja wykonuje kopię bitową.

Aby uzyskać informacje dotyczące wykonywania tej i innych funkcji pomocnika, zobacz artykuł [kolekcji: Jak utworzyć kolekcję bezpieczny](../how-to-make-a-type-safe-collection.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxtempl.h

##  <a name="dumpelements"></a>  Dumpelements —

Udostępnia zorientowane na strumień diagnostyczne dane wyjściowe w postaci tekstu dla elementów kolekcji w przypadku przesłonięcia.

```
template<class TYPE>
void  AFXAPI DumpElements(
    CDumpContext& dc,
    const TYPE* pElements,
    INT_PTR nCount);
```

### <a name="parameters"></a>Parametry

*dc*<br/>
Zrzuć kontekstu służąca do zrzucania elementów.

*TYP*<br/>
Parametr szablonu określający typ elementów.

*pElements*<br/>
Wskaźnik elementów można utworzyć zrzutu.

*nCount*<br/>
Liczba elementów, które można utworzyć zrzutu.

### <a name="remarks"></a>Uwagi

`CArray::Dump`, `CList::Dump`, I `CMap::Dump` funkcje wywołań, to jeśli głębokość zrzutu jest większa niż 0.

Domyślna implementacja nic nie robi. Jeśli elementy kolekcji są uzyskiwane z `CObject`, przesłonięcia zazwyczaj iteracji przez elementy kolekcji, wywołanie `Dump` dla każdego elementu w pozycji.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxtempl.h

##  <a name="hashkey"></a>  HashKey —

Oblicza wartość skrótu dla danego klucza.

```
template<class ARG_KEY>
AFX_INLINE UINT AFXAPI HashKey(ARG_KEY  key);
```

### <a name="parameters"></a>Parametry

*ARG_KEY*<br/>
Parametr szablonu określający typ danych, używane do dostępu do kluczy mapy.

*Klucz*<br/>
Klucz, którego wartość skrótu, które ma zostać obliczona.

### <a name="return-value"></a>Wartość zwracana

Wartość skrótu klucza.

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana bezpośrednio przez [CMap::RemoveKey](cmap-class.md#removekey) i pośrednio [CMap::Lookup](cmap-class.md#lookup) i [CMap::Operator &#91; &#93; ](cmap-class.md#operator_at).

Domyślna implementacja tworzy wartość skrótu, przesuwając *klucz* bezpośrednio przez cztery pozycji. Należy przesłonić tę funkcję, dzięki którym zwraca wartości skrótu w odpowiedni dla aplikacji.

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

##  <a name="serializeelements"></a>  Serializeelements —

[CArray](carray-class.md), [CList](clist-class.md), i [CMap](cmap-class.md) Wywołaj tę funkcję do serializowania elementów.

```
template<class TYPE>
void AFXAPI SerializeElements(CArchive& ar, TYPE* pElements, INT_PTR nCount);
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów.

*ar*<br/>
Obiekt archiwum do archiwizacji lub wejściowych.

*pElements*<br/>
Wskaźnik elementów archiwizowane.

*nCount*<br/>
Liczba elementów jest zarchiwizowany

### <a name="remarks"></a>Uwagi

Domyślna implementacja jest bitową operację odczytu lub zapisu.

Aby uzyskać informacje dotyczące wykonywania tej i innych funkcji pomocnika, zobacz artykuł [kolekcji: Jak utworzyć kolekcję bezpieczny](../how-to-make-a-type-safe-collection.md).

### <a name="example"></a>Przykład

Zobacz przykład w artykule [kolekcji: Jak utworzyć kolekcję bezpieczny](../how-to-make-a-type-safe-collection.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxtempl.h

## <a name="see-also"></a>Zobacz także

[Makra i funkcje globalne](mfc-macros-and-globals.md)<br/>
[Klasa CMap](cmap-class.md)<br/>
[Klasa CList](clist-class.md)<br/>
[Klasa CArray](carray-class.md)
