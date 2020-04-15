---
title: Klasa CObList
ms.date: 11/04/2016
f1_keywords:
- CObList
- AFXCOLL/CObList
- AFXCOLL/CObList::CObList
- AFXCOLL/CObList::AddHead
- AFXCOLL/CObList::AddTail
- AFXCOLL/CObList::Find
- AFXCOLL/CObList::FindIndex
- AFXCOLL/CObList::GetAt
- AFXCOLL/CObList::GetCount
- AFXCOLL/CObList::GetHead
- AFXCOLL/CObList::GetHeadPosition
- AFXCOLL/CObList::GetNext
- AFXCOLL/CObList::GetPrev
- AFXCOLL/CObList::GetSize
- AFXCOLL/CObList::GetTail
- AFXCOLL/CObList::GetTailPosition
- AFXCOLL/CObList::InsertAfter
- AFXCOLL/CObList::InsertBefore
- AFXCOLL/CObList::IsEmpty
- AFXCOLL/CObList::RemoveAll
- AFXCOLL/CObList::RemoveAt
- AFXCOLL/CObList::RemoveHead
- AFXCOLL/CObList::RemoveTail
- AFXCOLL/CObList::SetAt
helpviewer_keywords:
- CObList [MFC], CObList
- CObList [MFC], AddHead
- CObList [MFC], AddTail
- CObList [MFC], Find
- CObList [MFC], FindIndex
- CObList [MFC], GetAt
- CObList [MFC], GetCount
- CObList [MFC], GetHead
- CObList [MFC], GetHeadPosition
- CObList [MFC], GetNext
- CObList [MFC], GetPrev
- CObList [MFC], GetSize
- CObList [MFC], GetTail
- CObList [MFC], GetTailPosition
- CObList [MFC], InsertAfter
- CObList [MFC], InsertBefore
- CObList [MFC], IsEmpty
- CObList [MFC], RemoveAll
- CObList [MFC], RemoveAt
- CObList [MFC], RemoveHead
- CObList [MFC], RemoveTail
- CObList [MFC], SetAt
ms.assetid: 80699c93-33d8-4f8b-b8cf-7b58aeab64ca
ms.openlocfilehash: cccd45bf5a97ae7dcc8369015e0a431b3a9e960f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360369"
---
# <a name="coblist-class"></a>Klasa CObList

fWsuchza uporządkowane listy `CObject` wskaźników nieunikalnych dostępnych sekwencyjnie lub według wartości wskaźnika.

## <a name="syntax"></a>Składnia

```
class CObList : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Lista CObList::CObList](#coblist)|Tworzy pustą listę `CObject` wskaźników.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Lista CObList::AddHead](#addhead)|Dodaje element (lub wszystkie elementy na innej liście) do głowy listy (tworzy nową głowę).|
|[Lista CObList:::Dodajtail](#addtail)|Dodaje element (lub wszystkie elementy na innej liście) do ogona listy (tworzy nowy ogon).|
|[Lista CObList::Znajdź](#find)|Pobiera położenie elementu określonego przez wartość wskaźnika.|
|[Lista CObList::FindIndex](#findindex)|Pobiera położenie elementu określonego przez indeks oparty na wartości zero.|
|[Lista CObList::GetAt](#getat)|Pobiera element w danej pozycji.|
|[Lista CObList::GetCount](#getcount)|Zwraca liczbę elementów na tej liście.|
|[Lista CObList::GetHead](#gethead)|Zwraca element head listy (nie może być pusty).|
|[Lista CObList::GetHeadPosition](#getheadposition)|Zwraca położenie elementu head listy.|
|[Lista CObList::GetNext](#getnext)|Pobiera następny element do iteracji.|
|[Lista CObList::GetPrev](#getprev)|Pobiera poprzedni element do iteracji.|
|[Lista CObList::GetSize](#getsize)|Zwraca liczbę elementów na tej liście.|
|[Lista CObList::GetTail](#gettail)|Zwraca element ogonowy listy (nie może być pusty).|
|[Lista CObList::GetTailPosition](#gettailposition)|Zwraca położenie elementu ogonowego listy.|
|[CObList::WstawianiePo](#insertafter)|Wstawia nowy element po danej pozycji.|
|[CObList::WstawianiePrzed](#insertbefore)|Wstawia nowy element przed danym pozycją.|
|[CObList::IsEmpty](#isempty)|Testy stanu pustej listy (bez elementów).|
|[Lista CObList::Usuń wszystko](#removeall)|Usuwa wszystkie elementy z tej listy.|
|[CObList::Usuńat](#removeat)|Usuwa element z tej listy, określony przez położenie.|
|[CObList::Usuńgłowy](#removehead)|Usuwa element z głowy listy.|
|[Lista CObList::Usuńtail](#removetail)|Usuwa element z ogona listy.|
|[CObList::SetAt](#setat)|Ustawia element w danej pozycji.|

## <a name="remarks"></a>Uwagi

`CObList`listy zachowują się jak listy podwójnie połączone.

Zmienna typu POSITION jest kluczem listy. Zmienną POSITION można używać zarówno jako iteratora do przechodzenia przez listę sekwencyjnie, jak i jako zakładki do przechowywania miejsca. Pozycja nie jest jednak taka sama jak indeks.

Wstawianie elementu jest bardzo szybkie na głowicy listy, na ogonie i w znanej pozycji. Wyszukiwanie sekwencyjne jest konieczne, aby wyszukać element według wartości lub indeksu. To wyszukiwanie może być powolne, jeśli lista jest długa.

`CObList`zawiera makro IMPLEMENT_SERIAL w celu wspierania serializacji i dumpingu jego elementów. Jeśli lista `CObject` wskaźników jest przechowywana w archiwum, za pomocą przeciążonego `Serialize` operatora wstawiania lub funkcji elementu członkowskiego, każdy `CObject` element jest serializowany z kolei.

Jeśli potrzebujesz zrzutu `CObject` poszczególnych elementów na liście, należy ustawić głębokość kontekstu zrzutu na 1 lub większą.

Po `CObList` usunięciu obiektu lub usunięciu jego elementów `CObject` usuwane są tylko wskaźniki, a nie obiekty, do których się odwołują.

Możesz czerpać własne klasy `CObList`z . Nowa klasa listy, przeznaczone do przechowywania wskaźników `CObject`do obiektów pochodzących z , dodaje nowe elementy członkowskie danych i nowe funkcje członkowskie. Należy zauważyć, że wynikowa lista nie jest ściśle typu `CObject` bezpieczne, ponieważ umożliwia wstawianie dowolnego wskaźnika.

> [!NOTE]
> Aby przeprowadzić serializację listy, należy użyć makra [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) w implementacji klasy pochodnej.

Aby uzyskać więcej `CObList`informacji na temat korzystania z programu , zobacz artykuł [Kolekcje](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CObList`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcoll.h

## <a name="coblistaddhead"></a><a name="addhead"></a>Lista CObList::AddHead

Dodaje nowy element lub listę elementów do głowy tej listy.

```
POSITION AddHead(CObject* newElement);
void AddHead(CObList* pNewList);
```

### <a name="parameters"></a>Parametry

*nowyElement*<br/>
Wskaźnik, `CObject` który ma zostać dodany do tej listy.

*pNowa Lista*<br/>
Wskaźnik do `CObList` innej listy. Elementy w *pNewList* zostaną dodane do tej listy.

### <a name="return-value"></a>Wartość zwracana

Pierwsza wersja zwraca wartość POSITION nowo wstawionego elementu.

W poniższej tabeli przedstawiono `CObList::AddHead`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cptrlist](../../mfc/reference/cptrlist-class.md)|**POZYCJA AddHead( void** <strong>\*</strong> `newElement` **);**<br /><br /> **void AddHead( CPtrList** <strong>\*</strong> `pNewList` **);**|
|[Lista sznurów](../../mfc/reference/cstringlist-class.md)|**POZYCJA AddHead(const CString&** `newElement` **);**<br /><br /> **POZYCJA AddHead(LPCTSTR);** `newElement` **);**<br /><br /> **void AddHead (CStringList);** <strong>\*</strong> `pNewList` **);**|

### <a name="remarks"></a>Uwagi

Lista może być pusta przed operacją.

### <a name="example"></a>Przykład

  Zobacz [CObList::CObList](#coblist) dla listy `CAge` klasy.

[!code-cpp[NVC_MFCCollections#89](../../mfc/codesnippet/cpp/coblist-class_1.cpp)]

Wyniki tego programu są następujące:

```Output
AddHead example: A CObList with 2 elements
a CAge at $44A8 40
a CAge at $442A 21
```

## <a name="coblistaddtail"></a><a name="addtail"></a>Lista CObList:::Dodajtail

Dodaje nowy element lub listę elementów do ogona tej listy.

```
POSITION AddTail(CObject* newElement);
void AddTail(CObList* pNewList);
```

### <a name="parameters"></a>Parametry

*nowyElement*<br/>
Wskaźnik, `CObject` który ma zostać dodany do tej listy.

*pNowa Lista*<br/>
Wskaźnik do `CObList` innej listy. Elementy w *pNewList* zostaną dodane do tej listy.

### <a name="return-value"></a>Wartość zwracana

Pierwsza wersja zwraca wartość POSITION nowo wstawionego elementu.

### <a name="remarks"></a>Uwagi

Lista może być pusta przed operacją.

W poniższej tabeli przedstawiono `CObList::AddTail`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cptrlist](../../mfc/reference/cptrlist-class.md)|**POZYCJA AddTail( void** <strong>\*</strong> `newElement` **);**<br /><br /> **void AddTail( CPtrList** <strong>\*</strong> `pNewList` **);**|
|[Lista sznurów](../../mfc/reference/cstringlist-class.md)|**POZYCJA AddTail( const CString&** `newElement` **);**<br /><br /> **POZYCJA AddTail( LPCTSTR** `newElement` **);**<br /><br /> **void AddTail( CStringList** <strong>\*</strong> `pNewList` **);**|

### <a name="example"></a>Przykład

  Zobacz [CObList::CObList](#coblist) dla listy `CAge` klasy.

[!code-cpp[NVC_MFCCollections#90](../../mfc/codesnippet/cpp/coblist-class_2.cpp)]

Wyniki tego programu są następujące:

```Output
AddTail example: A CObList with 2 elements
a CAge at $444A 21
a CAge at $4526 40
```

## <a name="coblistcoblist"></a><a name="coblist"></a>Lista CObList::CObList

Tworzy pustą `CObject` listę wskaźników.

```
CObList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Parametry

*nBlockSize (Rozmiar)*<br/>
Szczegółowość alokacji pamięci w celu rozszerzenia listy.

### <a name="remarks"></a>Uwagi

Wraz z rozwojem listy pamięć jest przydzielana w jednostkach wpisów *nBlockSize.* Jeśli alokacja pamięci `CMemoryException` nie powiedzie się, a jest generowany.

W poniższej tabeli przedstawiono `CObList::CObList`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cptrlist](../../mfc/reference/cptrlist-class.md)|**CPtrList( INT_PTR** `nBlockSize` **= 10 );**|
|[Lista sznurów](../../mfc/reference/cstringlist-class.md)|**CStringList( INT_PTR** `nBlockSize` **= 10 );**|

### <a name="example"></a>Przykład

  Poniżej znajduje się `CObject`lista klasy `CAge` pochodnej używanej we wszystkich przykładach kolekcji:

[!code-cpp[NVC_MFCCollections#91](../../mfc/codesnippet/cpp/coblist-class_3.h)]

Poniżej znajduje `CObList` się przykład użycia konstruktora:

[!code-cpp[NVC_MFCCollections#92](../../mfc/codesnippet/cpp/coblist-class_4.cpp)]

## <a name="coblistfind"></a><a name="find"></a>Lista CObList::Znajdź

Przeszukuje listę sekwencyjnie, aby znaleźć pierwszy `CObject` wskaźnik pasujący do określonego `CObject` wskaźnika.

```
POSITION Find(
    CObject* searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>Parametry

*wyszukiwanieValue*<br/>
Wskaźnik obiektu, który ma być znaleziony na tej liście.

*startPoteru*<br/>
Pozycja początkowa wyszukiwania.

### <a name="return-value"></a>Wartość zwracana

Wartość POSITION, która może służyć do iteracji lub pobierania wskaźnika obiektu; NULL, jeśli obiekt nie zostanie znaleziony.

### <a name="remarks"></a>Uwagi

Należy zauważyć, że wartości wskaźnika są porównywane, a nie zawartość obiektów.

W poniższej tabeli przedstawiono `CObList::Find`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cptrlist](../../mfc/reference/cptrlist-class.md)|**POZYCJA Znajdź( nieważne** <strong>\*</strong> `searchValue` **, POZYCJA** `startAfter` **= NULL ) const;**|
|[Lista sznurów](../../mfc/reference/cstringlist-class.md)|**POZYCJA Znajdź( LPCTSTR** `searchValue` **, POSITION** `startAfter` **= NULL ) const;**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](#coblist) dla listy `CAge` klasy.

[!code-cpp[NVC_MFCCollections#93](../../mfc/codesnippet/cpp/coblist-class_5.cpp)]

## <a name="coblistfindindex"></a><a name="findindex"></a>Lista CObList::FindIndex

Używa wartości *nIndex* jako indeksu na liście.

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks od zera elementu listy, który ma zostać znaleziony.

### <a name="return-value"></a>Wartość zwracana

Wartość POSITION, która może służyć do iteracji lub pobierania wskaźnika obiektu; NULL if *nIndex* jest za duży. (Struktura generuje potwierdzenie, jeśli *nIndex* jest ujemny.)

### <a name="remarks"></a>Uwagi

Rozpoczyna skanowanie sekwencyjne z głowy listy, zatrzymując się na *n*th element.

W poniższej tabeli przedstawiono `CObList::FindIndex`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cptrlist](../../mfc/reference/cptrlist-class.md)|**POZYCJA FindIndex( INT_PTR** `nIndex` **) const;**|
|[Lista sznurów](../../mfc/reference/cstringlist-class.md)|**POZYCJA FindIndex( INT_PTR** `nIndex` **) const;**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](#coblist) dla listy `CAge` klasy.

[!code-cpp[NVC_MFCCollections#94](../../mfc/codesnippet/cpp/coblist-class_6.cpp)]

## <a name="coblistgetat"></a><a name="getat"></a>Lista CObList::GetAt

Zmienna typu POSITION jest kluczem listy.

```
CObject*& GetAt(POSITION position);
const CObject*& GetAt(POSITION position) const;
```

### <a name="parameters"></a>Parametry

*Pozycji*<br/>
Wartość POSITION zwrócona `GetHeadPosition` przez `Find` poprzednie wywołanie funkcji lub element członkowski.

### <a name="return-value"></a>Wartość zwracana

Zobacz opis wartości zwracanej dla [GetHead](#gethead).

### <a name="remarks"></a>Uwagi

To nie jest to samo co indeks i nie można obsługiwać na position wartość samodzielnie. `GetAt`pobiera `CObject` wskaźnik skojarzony z danym pozycją.

Należy upewnić się, że wartość POSITION reprezentuje prawidłową pozycję na liście. Jeśli jest nieprawidłowa, wersja debugowania biblioteki klas programu Microsoft Foundation potwierdza.

W poniższej tabeli przedstawiono `CObList::GetAt`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cptrlist](../../mfc/reference/cptrlist-class.md)|**const\* void& GetAt( pozycja pozycji pozycji** ) *position* **const;**<br /><br /> **void\*& GetAt(** *pozycja* **pozycji );**|
|[Lista sznurów](../../mfc/reference/cstringlist-class.md)|**const CString& GetAt( pozycja położenia** *position* **) const;**<br /><br /> **CString& GetAt(** *pozycja* pozycji **);**|

### <a name="example"></a>Przykład

  Zobacz przykład [findindex](#findindex).

## <a name="coblistgetcount"></a><a name="getcount"></a>Lista CObList::GetCount

Pobiera liczbę elementów na tej liście.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość całkowita zawierająca liczbę elementów.

W poniższej tabeli przedstawiono `CObList::GetCount`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cptrlist](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetCount( ) const;**|
|[Lista sznurów](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetCount( ) const;**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](#coblist) dla listy `CAge` klasy.

[!code-cpp[NVC_MFCCollections#95](../../mfc/codesnippet/cpp/coblist-class_7.cpp)]

## <a name="coblistgethead"></a><a name="gethead"></a>Lista CObList::GetHead

Pobiera `CObject` wskaźnik, który reprezentuje element head tej listy.

```
CObject*& GetHead();
const CObject*& GetHead() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli lista jest dostępna za pomocą `const CObList`wskaźnika do , a następnie `GetHead` zwraca `CObject` wskaźnik. Dzięki temu funkcja ma być używana tylko po prawej stronie instrukcji przypisania i w ten sposób chroni listę przed modyfikacją.

Jeśli lista jest dostępna bezpośrednio lub za `CObList`pośrednictwem `GetHead` wskaźnika do `CObject` , a następnie zwraca odwołanie do wskaźnika. Dzięki temu funkcja ma być używana po obu stronach instrukcji przypisania, a tym samym umożliwia modyfikowanie wpisów listy.

### <a name="remarks"></a>Uwagi

Przed wywołaniem należy upewnić się, że lista nie jest pusta. `GetHead` Jeśli lista jest pusta, potwierdza to wersja debugowania biblioteki klas programu Microsoft Foundation. Użyj [IsEmpty,](#isempty) aby sprawdzić, czy lista zawiera elementy.

W poniższej tabeli przedstawiono `CObList::GetHead`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cptrlist](../../mfc/reference/cptrlist-class.md)|**const\* void& GetHead( ) const; void\*& GetHead( );**|
|[Lista sznurów](../../mfc/reference/cstringlist-class.md)|**const CString& GetHead( ) const; CString& GetHead( );**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](#coblist) dla listy `CAge` klasy.

Poniższy przykład ilustruje `GetHead` użycie po lewej stronie instrukcji przypisania.

[!code-cpp[NVC_MFCCollections#96](../../mfc/codesnippet/cpp/coblist-class_8.cpp)]

## <a name="coblistgetheadposition"></a><a name="getheadposition"></a>Lista CObList::GetHeadPosition

Pobiera pozycję elementu head tej listy.

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość POSITION, która może służyć do iteracji lub pobierania wskaźnika obiektu; NULL, jeśli lista jest pusta.

W poniższej tabeli przedstawiono `CObList::GetHeadPosition`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cptrlist](../../mfc/reference/cptrlist-class.md)|**POZYCJA GetHeadPosition( ) const;**|
|[Lista sznurów](../../mfc/reference/cstringlist-class.md)|**POZYCJA GetHeadPosition( ) const;**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](#coblist) dla listy `CAge` klasy.

[!code-cpp[NVC_MFCCollections#97](../../mfc/codesnippet/cpp/coblist-class_9.cpp)]

## <a name="coblistgetnext"></a><a name="getnext"></a>Lista CObList::GetNext

Pobiera element listy identyfikowany przez *rPosition*, `POSITION` a następnie ustawia *rPosition* do wartości następnego wpisu na liście.

```
CObject*& GetNext(POSITION& rPosition);
const CObject* GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parametry

*rPozycja*<br/>
Odwołanie do wartości POSITION zwróconej `GetNext` `GetHeadPosition`przez poprzednie , lub inne wywołanie funkcji elementu członkowskiego.

### <a name="return-value"></a>Wartość zwracana

Zobacz opis wartości zwracanej dla [GetHead](#gethead).

### <a name="remarks"></a>Uwagi

Można użyć `GetNext` w pętli iteracji do przodu, jeśli ustalisz pozycję początkową za pomocą połączenia lub `GetHeadPosition` `Find`.

Należy upewnić się, że wartość POSITION reprezentuje prawidłową pozycję na liście. Jeśli jest nieprawidłowa, wersja debugowania biblioteki klas programu Microsoft Foundation potwierdza.

Jeśli pobrany element jest ostatnim na liście, nowa wartość *rPosition* jest ustawiona na WARTOŚĆ NULL.

Możliwe jest usunięcie elementu podczas iteracji. Zobacz przykład [removeat](#removeat).

> [!NOTE]
> Od MFC 8.0 wersja const tej metody `const CObject*` została zmieniona, aby powrócić zamiast `const CObject*&`.  Ta zmiana została wprowadzą w celu dostosowania kompilatora do zgodności ze standardem C++.

W poniższej tabeli przedstawiono `CObList::GetNext`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cptrlist](../../mfc/reference/cptrlist-class.md)|`void*& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const void* GetNext( POSITION&` `rPosition` `) const;`|
|[Lista sznurów](../../mfc/reference/cstringlist-class.md)|`CString& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetNext( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>Przykład

  Zobacz [CObList::CObList](#coblist) dla listy `CAge` klasy.

[!code-cpp[NVC_MFCCollections#98](../../mfc/codesnippet/cpp/coblist-class_10.cpp)]

Wyniki tego programu są następujące:

```Output
a CAge at $479C 40
a CAge at $46C0 21
```

## <a name="coblistgetprev"></a><a name="getprev"></a>Lista CObList::GetPrev

Pobiera element listy identyfikowany przez *rPosition*, a następnie ustawia *rPosition* do wartości POSITION poprzedniego wpisu na liście.

```
CObject*& GetPrev(POSITION& rPosition);
const CObject* GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parametry

*rPozycja*<br/>
Odwołanie do wartości POSITION zwróconej `GetPrev` przez poprzednie lub inne wywołanie funkcji elementu członkowskiego.

### <a name="return-value"></a>Wartość zwracana

Zobacz opis wartości zwracanej dla [GetHead](#gethead).

### <a name="remarks"></a>Uwagi

Można użyć `GetPrev` w pętli reverse iteracji, jeśli ustalisz `GetTailPosition` `Find`pozycję początkową za pomocą wywołania lub .

Należy upewnić się, że wartość POSITION reprezentuje prawidłową pozycję na liście. Jeśli jest nieprawidłowa, wersja debugowania biblioteki klas programu Microsoft Foundation potwierdza.

Jeśli pobrany element jest pierwszym na liście, nowa wartość *rPosition* jest ustawiona na WARTOŚĆ NULL.

> [!NOTE]
> Od MFC 8.0 wersja const tej metody `const CObject*` została zmieniona, aby powrócić zamiast `const CObject*&`.  Ta zmiana została wprowadzą w celu dostosowania kompilatora do zgodności ze standardem C++.

W poniższej tabeli przedstawiono `CObList::GetPrev`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cptrlist](../../mfc/reference/cptrlist-class.md)|`void*& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const void* GetPrev( POSITION&` `rPosition` `) const;`|
|[Lista sznurów](../../mfc/reference/cstringlist-class.md)|`CString& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetPrev( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>Przykład

  Zobacz [CObList::CObList](#coblist) dla listy `CAge` klasy.

[!code-cpp[NVC_MFCCollections#99](../../mfc/codesnippet/cpp/coblist-class_11.cpp)]

Wyniki tego programu są następujące:

```Output
a CAge at $421C 21
a CAge at $421C 40
```

## <a name="coblistgetsize"></a><a name="getsize"></a>Lista CObList::GetSize

Zwraca liczbę elementów listy.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Wartość zwracana

liczba elementów na liście.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby pobrać liczbę elementów na liście.

W poniższej tabeli przedstawiono `CObList::GetSize`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cptrlist](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetSize( ) const;**|
|[Lista sznurów](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetSize( ) const;**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](#coblist) dla listy `CAge` klasy.

[!code-cpp[NVC_MFCCollections#100](../../mfc/codesnippet/cpp/coblist-class_12.cpp)]

## <a name="coblistgettail"></a><a name="gettail"></a>Lista CObList::GetTail

Pobiera `CObject` wskaźnik, który reprezentuje element ogona tej listy.

```
CObject*& GetTail();
const CObject*& GetTail() const;
```

### <a name="return-value"></a>Wartość zwracana

Zobacz opis wartości zwracanej dla [GetHead](#gethead).

### <a name="remarks"></a>Uwagi

Przed wywołaniem należy upewnić się, że lista nie jest pusta. `GetTail` Jeśli lista jest pusta, potwierdza to wersja debugowania biblioteki klas programu Microsoft Foundation. Użyj [IsEmpty,](#isempty) aby sprawdzić, czy lista zawiera elementy.

W poniższej tabeli przedstawiono `CObList::GetTail`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cptrlist](../../mfc/reference/cptrlist-class.md)|**const\* void& GetTail( ) const; void\*& GetTail( );**|
|[Lista sznurów](../../mfc/reference/cstringlist-class.md)|**const CString& GetTail( ) const; CString& GetTail( );**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](#coblist) dla listy `CAge` klasy.

[!code-cpp[NVC_MFCCollections#101](../../mfc/codesnippet/cpp/coblist-class_13.cpp)]

## <a name="coblistgettailposition"></a><a name="gettailposition"></a>Lista CObList::GetTailPosition

Pobiera położenie elementu ogona tej listy; **NULL,** jeśli lista jest pusta.

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość POSITION, która może służyć do iteracji lub pobierania wskaźnika obiektu; NULL, jeśli lista jest pusta.

W poniższej tabeli przedstawiono `CObList::GetTailPosition`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cptrlist](../../mfc/reference/cptrlist-class.md)|**POZYCJA GetTailPosition( ) const;**|
|[Lista sznurów](../../mfc/reference/cstringlist-class.md)|**POZYCJA GetTailPosition( ) const;**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](#coblist) dla listy `CAge` klasy.

[!code-cpp[NVC_MFCCollections#102](../../mfc/codesnippet/cpp/coblist-class_14.cpp)]

## <a name="coblistinsertafter"></a><a name="insertafter"></a>CObList::WstawianiePo

Dodaje element do tej listy po elemencie w określonym położeniu.

```
POSITION InsertAfter(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>Parametry

*Pozycji*<br/>
Wartość POSITION zwrócona `GetNext`przez `GetPrev`poprzednie `Find` , lub wywołanie funkcji elementu członkowskiego.

*nowyElement*<br/>
Wskaźnik obiektu, który ma zostać dodany do tej listy.

W poniższej tabeli przedstawiono `CObList::InsertAfter`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cptrlist](../../mfc/reference/cptrlist-class.md)|**POZYCJA InsertPo(pozycja położenia,** *position* **nieważne** <strong>\*</strong> `newElement` **);**|
|[Lista sznurów](../../mfc/reference/cstringlist-class.md)|**Pozycja InsertPo(pozycja pozycji,** *position* **const CString&** `newElement` **);**<br /><br /> **POZYCJA InsertPo(pozycja pozycji,** *position* **LPCTSTR);** `newElement` **);**|

### <a name="return-value"></a>Wartość zwracana

Wartość POSITION, która jest taka sama jak parametr *position.*

### <a name="example"></a>Przykład

  Zobacz [CObList::CObList](#coblist) dla listy `CAge` klasy.

[!code-cpp[NVC_MFCCollections#103](../../mfc/codesnippet/cpp/coblist-class_15.cpp)]

Wyniki tego programu są następujące:

```Output
InsertAfter example: A CObList with 3 elements
a CAge at $4A44 40
a CAge at $4A64 65
a CAge at $4968 21
```

## <a name="coblistinsertbefore"></a><a name="insertbefore"></a>CObList::WstawianiePrzed

Dodaje element do tej listy przed elementem w określonym położeniu.

```
POSITION InsertBefore(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>Parametry

*Pozycji*<br/>
Wartość POSITION zwrócona `GetNext`przez `GetPrev`poprzednie `Find` , lub wywołanie funkcji elementu członkowskiego.

*nowyElement*<br/>
Wskaźnik obiektu, który ma zostać dodany do tej listy.

### <a name="return-value"></a>Wartość zwracana

Wartość POSITION, która może służyć do iteracji lub pobierania wskaźnika obiektu; NULL, jeśli lista jest pusta.

W poniższej tabeli przedstawiono `CObList::InsertBefore`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cptrlist](../../mfc/reference/cptrlist-class.md)|**POZYCJA InsertBefore( pozycja położenia, nieważne** *position* **, void** <strong>\*</strong> `newElement` **);**|
|[Lista sznurów](../../mfc/reference/cstringlist-class.md)|**POZYCJA InsertBefore( pozycja położenia,** *position* **const CString&** `newElement` **);**<br /><br /> **POZYCJA InsertBefore(** *pozycja* **pozycji, LPCTSTR** `newElement` **);**|

### <a name="example"></a>Przykład

  Zobacz [CObList::CObList](#coblist) dla listy `CAge` klasy.

[!code-cpp[NVC_MFCCollections#104](../../mfc/codesnippet/cpp/coblist-class_16.cpp)]

Wyniki tego programu są następujące:

```Output
InsertBefore example: A CObList with 3 elements
a CAge at $4AE2 40
a CAge at $4B02 65
a CAge at $49E6 21
```

## <a name="coblistisempty"></a><a name="isempty"></a>CObList::IsEmpty

Wskazuje, czy ta lista nie zawiera żadnych elementów.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli ta lista jest pusta; w przeciwnym razie 0.

W poniższej tabeli przedstawiono `CObList::IsEmpty`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cptrlist](../../mfc/reference/cptrlist-class.md)|**BOOL IsEmpty( ) const;**|
|[Lista sznurów](../../mfc/reference/cstringlist-class.md)|**BOOL IsEmpty( ) const;**|

### <a name="example"></a>Przykład

  Zobacz przykład [RemoveAll](#removeall).

## <a name="coblistremoveall"></a><a name="removeall"></a>Lista CObList::Usuń wszystko

Usuwa wszystkie elementy z tej listy i `CObList` zwalnia skojarzoną pamięć.

```
void RemoveAll();
```

### <a name="remarks"></a>Uwagi

Jeśli lista jest już pusta, nie jest generowany żaden błąd.

Usunięcie elementów z `CObList`programu powoduje usunięcie wskaźników obiektów z listy. Twoim obowiązkiem jest usunięcie samych obiektów.

W poniższej tabeli przedstawiono `CObList::RemoveAll`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cptrlist](../../mfc/reference/cptrlist-class.md)|**void RemoveAll( );**|
|[Lista sznurów](../../mfc/reference/cstringlist-class.md)|**void RemoveAll( );**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](#coblist) dla listy `CAge` klasy.

[!code-cpp[NVC_MFCCollections#105](../../mfc/codesnippet/cpp/coblist-class_17.cpp)]

## <a name="coblistremoveat"></a><a name="removeat"></a>CObList::Usuńat

Usuwa określony element z tej listy.

```
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>Parametry

*Pozycji*<br/>
Położenie elementu, który ma zostać usunięty z listy.

### <a name="remarks"></a>Uwagi

Usunięcie elementu z `CObList`elementu powoduje usunięcie wskaźnika obiektu z listy. Twoim obowiązkiem jest usunięcie samych obiektów.

Należy upewnić się, że wartość POSITION reprezentuje prawidłową pozycję na liście. Jeśli jest nieprawidłowa, wersja debugowania biblioteki klas programu Microsoft Foundation potwierdza.

W poniższej tabeli przedstawiono `CObList::RemoveAt`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cptrlist](../../mfc/reference/cptrlist-class.md)|**void RemoveAt( pozycja położenia);** *position* **);**|
|[Lista sznurów](../../mfc/reference/cstringlist-class.md)|**void RemoveAt( pozycja położenia);** *position* **);**|

### <a name="example"></a>Przykład

  Należy zachować ostrożność podczas usuwania elementu podczas iteracji listy. W poniższym przykładzie przedstawiono technikę usuwania, która gwarantuje prawidłową wartość **POSITION** dla [GetNext](#getnext).

Zobacz [CObList::CObList](#coblist) dla listy `CAge` klasy.

[!code-cpp[NVC_MFCCollections#106](../../mfc/codesnippet/cpp/coblist-class_18.cpp)]

Wyniki tego programu są następujące:

`RemoveAt example: A CObList with 2 elements`

`a CAge at $4C1E 65`

`a CAge at $4B22 21`

## <a name="coblistremovehead"></a><a name="removehead"></a>CObList::Usuńgłowy

Usuwa element z głowy listy i zwraca do niego wskaźnik.

```
CObject* RemoveHead();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik `CObject` wcześniej na czele listy.

### <a name="remarks"></a>Uwagi

Przed wywołaniem należy upewnić się, że lista nie jest pusta. `RemoveHead` Jeśli lista jest pusta, potwierdza to wersja debugowania biblioteki klas programu Microsoft Foundation. Użyj [IsEmpty,](#isempty) aby sprawdzić, czy lista zawiera elementy.

W poniższej tabeli przedstawiono `CObList::RemoveHead`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cptrlist](../../mfc/reference/cptrlist-class.md)|**void\* RemoveHead( );**|
|[Lista sznurów](../../mfc/reference/cstringlist-class.md)|**CString RemoveHead( );**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](#coblist) dla listy `CAge` klasy.

[!code-cpp[NVC_MFCCollections#107](../../mfc/codesnippet/cpp/coblist-class_19.cpp)]

## <a name="coblistremovetail"></a><a name="removetail"></a>Lista CObList::Usuńtail

Usuwa element z ogona listy i zwraca do niego wskaźnik.

```
CObject* RemoveTail();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu, który znajdował się na ogonie listy.

### <a name="remarks"></a>Uwagi

Przed wywołaniem należy upewnić się, że lista nie jest pusta. `RemoveTail` Jeśli lista jest pusta, potwierdza to wersja debugowania biblioteki klas programu Microsoft Foundation. Użyj [IsEmpty,](#isempty) aby sprawdzić, czy lista zawiera elementy.

W poniższej tabeli przedstawiono `CObList::RemoveTail`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cptrlist](../../mfc/reference/cptrlist-class.md)|**void\* RemoveTail( );**|
|[Lista sznurów](../../mfc/reference/cstringlist-class.md)|**CString RemoveTail( );**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](#coblist) dla listy `CAge` klasy.

[!code-cpp[NVC_MFCCollections#108](../../mfc/codesnippet/cpp/coblist-class_20.cpp)]

## <a name="coblistsetat"></a><a name="setat"></a>CObList::SetAt

Ustawia element w danej pozycji.

```
void SetAt(
    POSITION pos,
    CObject* newElement);
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Położenie elementu, który ma być ustawiony.

*nowyElement*<br/>
Wskaźnik, `CObject` który ma zostać zapisany na liście.

### <a name="remarks"></a>Uwagi

Zmienna typu POSITION jest kluczem listy. To nie jest to samo co indeks i nie można obsługiwać na position wartość samodzielnie. `SetAt`zapisuje `CObject` wskaźnik do określonej pozycji na liście.

Należy upewnić się, że wartość POSITION reprezentuje prawidłową pozycję na liście. Jeśli jest nieprawidłowa, wersja debugowania biblioteki klas programu Microsoft Foundation potwierdza.

W poniższej tabeli przedstawiono `CObList::SetAt`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cptrlist](../../mfc/reference/cptrlist-class.md)|**void SetAt( POZYCJA** `pos` **, const CString&** `newElement` **);**|
|[Lista sznurów](../../mfc/reference/cstringlist-class.md)|**void SetAt( POZYCJA** `pos` **, LPCTSTR** `newElement` **);**|

### <a name="example"></a>Przykład

  Zobacz [CObList::CObList](#coblist) dla listy `CAge` klasy.

[!code-cpp[NVC_MFCCollections#109](../../mfc/codesnippet/cpp/coblist-class_21.cpp)]

Wyniki tego programu są następujące:

```Output
SetAt example: A CObList with 2 elements
a CAge at $4D98 40
a CAge at $4DB8 65
```

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CStringList](../../mfc/reference/cstringlist-class.md)<br/>
[Klasa CPtrList](../../mfc/reference/cptrlist-class.md)
