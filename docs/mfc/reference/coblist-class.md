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
ms.openlocfilehash: 2fc3a3643c675394de555f1411030e278bcee775
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855335"
---
# <a name="coblist-class"></a>Klasa CObList

fSupports uporządkowane listy nieunikatowych wskaźników `CObject` dostępnych sekwencyjnie lub według wartości wskaźnika.

## <a name="syntax"></a>Składnia

```
class CObList : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CObList::CObList](#coblist)|Tworzy pustą listę wskaźników `CObject`.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CObList:: addszef](#addhead)|Dodaje element (lub wszystkie elementy z innej listy) do nagłówka listy (tworzy nowy nagłówek).|
|[CObList:: AddTail](#addtail)|Dodaje element (lub wszystkie elementy z innej listy) do ogona listy (tworzy nowy ogon).|
|[CObList:: find](#find)|Pobiera pozycję elementu określonego przez wartość wskaźnika.|
|[CObList:: FindIndex —](#findindex)|Pobiera pozycję elementu określonego przez indeks (liczony od zera).|
|[CObList::GetAt](#getat)|Pobiera element w danym położeniu.|
|[CObList:: GetCount](#getcount)|Zwraca liczbę elementów na liście.|
|[CObList:: getszef](#gethead)|Zwraca element główny listy (nie może być pusty).|
|[CObList::GetHeadPosition](#getheadposition)|Zwraca pozycję elementu nagłówkowego listy.|
|[CObList:: GetNext](#getnext)|Pobiera następny element do iteracji.|
|[CObList:: getpoprz](#getprev)|Pobiera poprzedni element do iteracji.|
|[CObList:: GetSize](#getsize)|Zwraca liczbę elementów na liście.|
|[CObList:: GetTail](#gettail)|Zwraca element końcowy listy (nie może być pusty).|
|[CObList::GetTailPosition](#gettailposition)|Zwraca pozycję elementu ogona listy.|
|[CObList::InsertAfter](#insertafter)|Wstawia nowy element po danej pozycji.|
|[CObList::InsertBefore](#insertbefore)|Wstawia nowy element przed daną pozycją.|
|[CObList:: IsEmpty](#isempty)|Testy dla warunku pustej listy (brak elementów).|
|[CObList::](#removeall)|Usuwa wszystkie elementy z tej listy.|
|[CObList::RemoveAt](#removeat)|Usuwa element z tej listy, określony według pozycji.|
|[CObList::RemoveHead](#removehead)|Usuwa element z nagłówka listy.|
|[CObList::RemoveTail](#removetail)|Usuwa element z ogona listy.|
|[CObList::SetAt](#setat)|Ustawia element w danym położeniu.|

## <a name="remarks"></a>Uwagi

listy `CObList` zachowują się jak listy połączone podwójnie.

Zmienna typu pozycja jest kluczem dla listy. Można użyć zmiennej POSITION zarówno jako iteratora do przechodzenia listy sekwencyjnie i jako zakładki do przechowania miejsca. Pozycja nie jest jednak taka sama jak indeks.

Wstawianie elementów jest bardzo szybkie na początku listy, na końcu i na znanym miejscu. Wyszukiwanie sekwencyjne jest niezbędne do wyszukania elementu według wartości lub indeksu. To wyszukiwanie może być wolne, jeśli lista jest długa.

`CObList` zawiera IMPLEMENT_SERIAL makro do obsługi serializacji i dumpingu jego elementów. Jeśli lista wskaźników `CObject` jest przechowywana w archiwum, ze przeciążonym operatorem wstawiania lub z funkcją składową `Serialize`, każdy element `CObject` jest serializowany z kolei.

Jeśli potrzebujesz zrzutu poszczególnych elementów `CObject` na liście, musisz ustawić głębokość kontekstu zrzutu na 1 lub większą.

Po usunięciu obiektu `CObList` lub po usunięciu jego elementów zostaną usunięte tylko wskaźniki `CObject`, a nie obiekty, do których się odwołują.

Możesz utworzyć własne klasy z `CObList`. Nowa Klasa listy, przeznaczona do przechowywania wskaźników do obiektów pochodzących od `CObject`, dodaje nowe składowe danych i nowe funkcje członkowskie. Należy zauważyć, że lista wyników nie jest ściśle bezpieczna, ponieważ umożliwia wstawianie dowolnego `CObject` wskaźnika.

> [!NOTE]
>  Jeśli zamierzasz serializować listę, musisz użyć makra [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) w implementacji klasy pochodnej.

Aby uzyskać więcej informacji na temat korzystania z `CObList`, zobacz [kolekcje](../../mfc/collections.md)artykułów.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CObList`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcoll. h

##  <a name="addhead"></a>CObList:: addszef

Dodaje nowy element lub listę elementów do nagłówka tej listy.

```
POSITION AddHead(CObject* newElement);
void AddHead(CObList* pNewList);
```

### <a name="parameters"></a>Parametry

*newElement*<br/>
Wskaźnik `CObject`, który ma zostać dodany do tej listy.

*pNewList*<br/>
Wskaźnik do innej listy `CObList`. Elementy w *pNewList* zostaną dodane do tej listy.

### <a name="return-value"></a>Wartość zwracana

Pierwsza wersja zwraca wartość pozycji nowo wstawionego elementu.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObList::AddHead`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Pozycja addgłowy (void** <strong>\*</strong> `newElement` **);**<br /><br /> **void addszef (CPtrList** <strong>\*</strong> `pNewList` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Pozycja addgłowy (const CString &** `newElement` **);**<br /><br /> **Pozycja addgłowy (LPCTSTR** `newElement` **);**<br /><br /> **void addszef (CStringList** <strong>\*</strong> `pNewList` **);**|

### <a name="remarks"></a>Uwagi

Lista może być pusta przed operacją.

### <a name="example"></a>Przykład

  Aby uzyskać listę klasy `CAge`, zobacz [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#89](../../mfc/codesnippet/cpp/coblist-class_1.cpp)]

Wyniki z tego programu są następujące:

```Output
AddHead example: A CObList with 2 elements
a CAge at $44A8 40
a CAge at $442A 21
```

##  <a name="addtail"></a>CObList:: AddTail

Dodaje nowy element lub listę elementów do ogona tej listy.

```
POSITION AddTail(CObject* newElement);
void AddTail(CObList* pNewList);
```

### <a name="parameters"></a>Parametry

*newElement*<br/>
Wskaźnik `CObject`, który ma zostać dodany do tej listy.

*pNewList*<br/>
Wskaźnik do innej listy `CObList`. Elementy w *pNewList* zostaną dodane do tej listy.

### <a name="return-value"></a>Wartość zwracana

Pierwsza wersja zwraca wartość pozycji nowo wstawionego elementu.

### <a name="remarks"></a>Uwagi

Lista może być pusta przed operacją.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObList::AddTail`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Pozycja AddTail (void** <strong>\*</strong> `newElement` **);**<br /><br /> **void AddTail (CPtrList** <strong>\*</strong> `pNewList` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Pozycja AddTail (const CString &** `newElement` **);**<br /><br /> **Pozycja AddTail (LPCTSTR** `newElement` **);**<br /><br /> **void AddTail (CStringList** <strong>\*</strong> `pNewList` **);**|

### <a name="example"></a>Przykład

  Aby uzyskać listę klasy `CAge`, zobacz [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#90](../../mfc/codesnippet/cpp/coblist-class_2.cpp)]

Wyniki z tego programu są następujące:

```Output
AddTail example: A CObList with 2 elements
a CAge at $444A 21
a CAge at $4526 40
```

##  <a name="coblist"></a>CObList::CObList

Tworzy pustą listę wskaźników `CObject`.

```
CObList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Parametry

*nBlockSize*<br/>
Stopień szczegółowości alokacji pamięci na potrzeby rozszerzania listy.

### <a name="remarks"></a>Uwagi

Gdy lista zostanie powiększona, pamięć jest przypisana w jednostkach wpisów *nBlockSize* . Jeśli alokacja pamięci nie powiedzie się, zostanie zgłoszony `CMemoryException`.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObList::CObList`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**CPtrList (INT_PTR** `nBlockSize` **= 10);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CStringList (INT_PTR** `nBlockSize` **= 10);**|

### <a name="example"></a>Przykład

  Poniżej znajduje się lista `CAge` klasy pochodnej `CObject`używana we wszystkich przykładach kolekcji:

[!code-cpp[NVC_MFCCollections#91](../../mfc/codesnippet/cpp/coblist-class_3.h)]

Poniżej znajduje się przykład użycia konstruktora `CObList`:

[!code-cpp[NVC_MFCCollections#92](../../mfc/codesnippet/cpp/coblist-class_4.cpp)]

##  <a name="find"></a>CObList:: find

Wyszukuje w kolejności na liście pierwszy `CObject` wskaźnik zgodny z określonym `CObject` wskaźnikiem.

```
POSITION Find(
    CObject* searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>Parametry

*searchValue*<br/>
Wskaźnik obiektu, który ma zostać odnaleziony na tej liście.

*startAfter*<br/>
Pozycja początkowa dla wyszukiwania.

### <a name="return-value"></a>Wartość zwracana

Wartość pozycji, która może być używana do pobierania iteracji lub wskaźnika obiektu; Wartość NULL, jeśli nie można odnaleźć obiektu.

### <a name="remarks"></a>Uwagi

Należy zauważyć, że wartości wskaźnika są porównywane, a nie zawartość obiektów.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObList::Find`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Pozycja Znajdź (void** <strong>\*</strong> `searchValue` **, Position** `startAfter` **= null) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Pozycja Find (LPCTSTR** `searchValue` **, Position** `startAfter` **= null) const;**|

### <a name="example"></a>Przykład

Aby uzyskać listę klasy `CAge`, zobacz [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#93](../../mfc/codesnippet/cpp/coblist-class_5.cpp)]

##  <a name="findindex"></a>CObList:: FindIndex —

Używa wartości *nIndex* jako indeksu do listy.

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks (liczony od zera) elementu listy, który ma zostać znaleziony.

### <a name="return-value"></a>Wartość zwracana

Wartość pozycji, która może być używana do pobierania iteracji lub wskaźnika obiektu; Wartość NULL, jeśli *nIndex* jest zbyt duża. (Struktura generuje potwierdzenie, jeśli *nIndex* jest ujemna).

### <a name="remarks"></a>Uwagi

Rozpocznie skanowanie sekwencyjne od szefa listy, zatrzymując na *n*-tym elemencie.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObList::FindIndex`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Position FindIndex — (INT_PTR** `nIndex` **) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Position FindIndex — (INT_PTR** `nIndex` **) const;**|

### <a name="example"></a>Przykład

Aby uzyskać listę klasy `CAge`, zobacz [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#94](../../mfc/codesnippet/cpp/coblist-class_6.cpp)]

##  <a name="getat"></a>CObList::GetAt

Zmienna typu pozycja jest kluczem dla listy.

```
CObject*& GetAt(POSITION position);
const CObject*& GetAt(POSITION position) const;
```

### <a name="parameters"></a>Parametry

*umieścić*<br/>
Wartość pozycji zwrócona przez poprzednie `GetHeadPosition` lub `Find` wywołanie funkcji składowej.

### <a name="return-value"></a>Wartość zwracana

Zobacz opis wartości zwracanej dla elementu [Getnagłówke](#gethead).

### <a name="remarks"></a>Uwagi

Nie jest taki sam jak indeks i nie można wykonać operacji na wartości pozycji samodzielnie. `GetAt` Pobiera wskaźnik `CObject` skojarzony z daną pozycją.

Musisz się upewnić, że wartość pozycji reprezentuje prawidłową pozycję na liście. Jeśli jest nieprawidłowa, wersja debugowana biblioteka MFC potwierdzenia.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObList::GetAt`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void\*& GetAt (** *pozycja* położenia **) stała;**<br /><br /> **void\*& GetAt (** *pozycja* położenia **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString & GetAt (** *pozycja* położenia **) stała;**<br /><br /> **CString & GetAt (** *pozycja* położenia **);**|

### <a name="example"></a>Przykład

  Zobacz przykład dla [FindIndex —](#findindex).

##  <a name="getcount"></a>CObList:: GetCount

Pobiera liczbę elementów na tej liście.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość całkowita zawierająca liczbę elementów.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObList::GetCount`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetCount () const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetCount () const;**|

### <a name="example"></a>Przykład

Aby uzyskać listę klasy `CAge`, zobacz [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#95](../../mfc/codesnippet/cpp/coblist-class_7.cpp)]

##  <a name="gethead"></a>CObList:: getszef

Pobiera `CObject` wskaźnik reprezentujący element nagłówka tej listy.

```
CObject*& GetHead();
const CObject*& GetHead() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli dostęp do listy jest uzyskiwany za pomocą wskaźnika do `const CObList`, `GetHead` zwraca wskaźnik `CObject`. Dzięki temu funkcja może być używana tylko po prawej stronie instrukcji przypisania i w ten sposób chroni listę przed modyfikacją.

Jeśli do listy jest uzyskiwany dostęp bezpośrednio lub za pomocą wskaźnika do `CObList`, `GetHead` zwraca odwołanie do wskaźnika `CObject`. Dzięki temu funkcja może być używana po obu stronach instrukcji przypisania i w ten sposób zezwala na modyfikowanie wpisów listy.

### <a name="remarks"></a>Uwagi

Przed wywołaniem `GetHead`należy upewnić się, że lista nie jest pusta. Jeśli lista jest pusta, wówczas wersja do debugowania biblioteka MFC potwierdzenia. Użyj [IsEmpty](#isempty) , aby sprawdzić, czy lista zawiera elementy.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObList::GetHead`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void\*& getnagłówku () const; void\*& getnagłówkowym ();**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString & getgłowy () const; CString & getszef ();**|

### <a name="example"></a>Przykład

Aby uzyskać listę klasy `CAge`, zobacz [CObList:: CObList](#coblist) .

Poniższy przykład ilustruje użycie `GetHead` po lewej stronie instrukcji przypisania.

[!code-cpp[NVC_MFCCollections#96](../../mfc/codesnippet/cpp/coblist-class_8.cpp)]

##  <a name="getheadposition"></a>CObList::GetHeadPosition

Pobiera pozycję elementu nagłówkowego tej listy.

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość pozycji, która może być używana do pobierania iteracji lub wskaźnika obiektu; Wartość NULL, jeśli lista jest pusta.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObList::GetHeadPosition`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION GetHeadPosition () const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION GetHeadPosition () const;**|

### <a name="example"></a>Przykład

Aby uzyskać listę klasy `CAge`, zobacz [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#97](../../mfc/codesnippet/cpp/coblist-class_9.cpp)]

##  <a name="getnext"></a>CObList:: GetNext

Pobiera element list identyfikowany przez *elemencie rPosition*, a następnie ustawia *elemencie rposition* na wartość `POSITION` następnego wpisu na liście.

```
CObject*& GetNext(POSITION& rPosition);
const CObject* GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parametry

*Elemencie rPosition*<br/>
Odwołanie do wartości pozycji zwróconej przez poprzednie `GetNext`, `GetHeadPosition`lub inne wywołanie funkcji elementu członkowskiego.

### <a name="return-value"></a>Wartość zwracana

Zobacz opis wartości zwracanej dla elementu [Getnagłówke](#gethead).

### <a name="remarks"></a>Uwagi

Możesz użyć `GetNext` w pętli iteracji do przodu, Jeśli ustanowisz początkową pozycję z wywołaniem do `GetHeadPosition` lub `Find`.

Musisz się upewnić, że wartość pozycji reprezentuje prawidłową pozycję na liście. Jeśli jest nieprawidłowa, wersja debugowana biblioteka MFC potwierdzenia.

Jeśli pobrany element jest ostatni na liście, Nowa wartość *elemencie rPosition* jest ustawiona na wartość null.

Istnieje możliwość usunięcia elementu podczas iteracji. Zobacz przykład dla [RemoveAt](#removeat).

> [!NOTE]
>  Począwszy od biblioteki MFC 8,0, wersja const tej metody zmieniła się na zwrócenie `const CObject*`, a nie `const CObject*&`.  Ta zmiana została wprowadzona w celu zapewnienia zgodności kompilatora ze C++ standardem.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObList::GetNext`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const void* GetNext( POSITION&` `rPosition` `) const;`|
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetNext( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>Przykład

  Aby uzyskać listę klasy `CAge`, zobacz [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#98](../../mfc/codesnippet/cpp/coblist-class_10.cpp)]

Wyniki z tego programu są następujące:

```Output
a CAge at $479C 40
a CAge at $46C0 21
```

##  <a name="getprev"></a>CObList:: getpoprz

Pobiera element list identyfikowany przez *elemencie rPosition*, a następnie ustawia *elemencie RPOSITION* na wartość pozycji poprzedniej pozycji na liście.

```
CObject*& GetPrev(POSITION& rPosition);
const CObject* GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parametry

*Elemencie rPosition*<br/>
Odwołanie do wartości pozycji zwróconej przez poprzednie `GetPrev` lub inne wywołanie funkcji składowej.

### <a name="return-value"></a>Wartość zwracana

Zobacz opis wartości zwracanej dla elementu [Getnagłówke](#gethead).

### <a name="remarks"></a>Uwagi

Można użyć `GetPrev` w pętli wstecznej iteracji, jeśli zostanie nadana początkowa pozycja z wywołaniem `GetTailPosition` lub `Find`.

Musisz się upewnić, że wartość pozycji reprezentuje prawidłową pozycję na liście. Jeśli jest nieprawidłowa, wersja debugowana biblioteka MFC potwierdzenia.

Jeśli pobrany element jest pierwszy na liście, Nowa wartość *elemencie rPosition* jest ustawiona na wartość null.

> [!NOTE]
>  Począwszy od biblioteki MFC 8,0, wersja const tej metody zmieniła się na zwrócenie `const CObject*`, a nie `const CObject*&`.  Ta zmiana została wprowadzona w celu zapewnienia zgodności kompilatora ze C++ standardem.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObList::GetPrev`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const void* GetPrev( POSITION&` `rPosition` `) const;`|
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetPrev( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>Przykład

  Aby uzyskać listę klasy `CAge`, zobacz [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#99](../../mfc/codesnippet/cpp/coblist-class_11.cpp)]

Wyniki z tego programu są następujące:

```Output
a CAge at $421C 21
a CAge at $421C 40
```

##  <a name="getsize"></a>CObList:: GetSize

Zwraca liczbę elementów listy.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów na liście.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby pobrać liczbę elementów na liście.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObList::GetSize`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetSize () const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetSize () const;**|

### <a name="example"></a>Przykład

Aby uzyskać listę klasy `CAge`, zobacz [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#100](../../mfc/codesnippet/cpp/coblist-class_12.cpp)]

##  <a name="gettail"></a>CObList:: GetTail

Pobiera `CObject` wskaźnik reprezentujący element ogona tej listy.

```
CObject*& GetTail();
const CObject*& GetTail() const;
```

### <a name="return-value"></a>Wartość zwracana

Zobacz opis wartości zwracanej dla elementu [Getnagłówke](#gethead).

### <a name="remarks"></a>Uwagi

Przed wywołaniem `GetTail`należy upewnić się, że lista nie jest pusta. Jeśli lista jest pusta, wówczas wersja do debugowania biblioteka MFC potwierdzenia. Użyj [IsEmpty](#isempty) , aby sprawdzić, czy lista zawiera elementy.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObList::GetTail`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void\*& GetTail () const; void\*& GetTail ();**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString & GetTail () const; CString & GetTail ();**|

### <a name="example"></a>Przykład

Aby uzyskać listę klasy `CAge`, zobacz [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#101](../../mfc/codesnippet/cpp/coblist-class_13.cpp)]

##  <a name="gettailposition"></a>CObList::GetTailPosition

Pobiera pozycję elementu końcowego z tej listy. **Wartość null** , jeśli lista jest pusta.

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość pozycji, która może być używana do pobierania iteracji lub wskaźnika obiektu; Wartość NULL, jeśli lista jest pusta.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObList::GetTailPosition`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION GetTailPosition () const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION GetTailPosition () const;**|

### <a name="example"></a>Przykład

Aby uzyskać listę klasy `CAge`, zobacz [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#102](../../mfc/codesnippet/cpp/coblist-class_14.cpp)]

##  <a name="insertafter"></a>CObList::InsertAfter

Dodaje element do tej listy po elemencie na określonej pozycji.

```
POSITION InsertAfter(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>Parametry

*umieścić*<br/>
Wartość pozycji zwrócona przez poprzednie `GetNext`, `GetPrev`lub `Find` wywołanie funkcji składowej.

*newElement*<br/>
Wskaźnik obiektu, który ma zostać dodany do tej listy.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObList::InsertAfter`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Pozycja InsertAfter (pozycja położenia** **, void** <strong>\*</strong> `newElement` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Position InsertAfter (położenie pozycji** **, const CString &** `newElement` **);**<br /><br /> **Position InsertAfter (położenie pozycji** **, LPCTSTR** `newElement` **);**|

### <a name="return-value"></a>Wartość zwracana

Wartość pozycji, która jest taka sama jak parametr *pozycji* .

### <a name="example"></a>Przykład

  Aby uzyskać listę klasy `CAge`, zobacz [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#103](../../mfc/codesnippet/cpp/coblist-class_15.cpp)]

Wyniki z tego programu są następujące:

```Output
InsertAfter example: A CObList with 3 elements
a CAge at $4A44 40
a CAge at $4A64 65
a CAge at $4968 21
```

##  <a name="insertbefore"></a>CObList::InsertBefore

Dodaje element do tej listy przed elementem w określonej pozycji.

```
POSITION InsertBefore(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>Parametry

*umieścić*<br/>
Wartość pozycji zwrócona przez poprzednie `GetNext`, `GetPrev`lub `Find` wywołanie funkcji składowej.

*newElement*<br/>
Wskaźnik obiektu, który ma zostać dodany do tej listy.

### <a name="return-value"></a>Wartość zwracana

Wartość pozycji, która może być używana do pobierania iteracji lub wskaźnika obiektu; Wartość NULL, jeśli lista jest pusta.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObList::InsertBefore`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Pozycja InsertBefore (pozycja położenia** **, void** <strong>\*</strong> `newElement` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Position InsertBefore (położenie pozycji** **, const CString &** `newElement` **);**<br /><br /> **Position InsertBefore (położenie pozycji** **, LPCTSTR** `newElement` **);**|

### <a name="example"></a>Przykład

  Aby uzyskać listę klasy `CAge`, zobacz [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#104](../../mfc/codesnippet/cpp/coblist-class_16.cpp)]

Wyniki z tego programu są następujące:

```Output
InsertBefore example: A CObList with 3 elements
a CAge at $4AE2 40
a CAge at $4B02 65
a CAge at $49E6 21
```

##  <a name="isempty"></a>CObList:: IsEmpty

Wskazuje, czy ta lista nie zawiera żadnych elementów.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli ta lista jest pusta; w przeciwnym razie 0.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObList::IsEmpty`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**BOOL IsEmpty () const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**BOOL IsEmpty () const;**|

### <a name="example"></a>Przykład

  Zobacz [przykład dla mnie](#removeall).

##  <a name="removeall"></a>CObList::

Usuwa wszystkie elementy z tej listy i zwalnia skojarzoną pamięć `CObList`.

```
void RemoveAll();
```

### <a name="remarks"></a>Uwagi

Nie Wygenerowano żadnego błędu, jeśli lista jest już pusta.

Po usunięciu elementów z `CObList`, można usunąć z listy wskaźniki obiektów. Ponosisz odpowiedzialność za usunięcie samych obiektów.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObList::RemoveAll`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void No();**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void No();**|

### <a name="example"></a>Przykład

Aby uzyskać listę klasy `CAge`, zobacz [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#105](../../mfc/codesnippet/cpp/coblist-class_17.cpp)]

##  <a name="removeat"></a>CObList::RemoveAt

Usuwa określony element z tej listy.

```
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>Parametry

*umieścić*<br/>
Pozycja elementu, który ma zostać usunięty z listy.

### <a name="remarks"></a>Uwagi

Usunięcie elementu z `CObList`powoduje usunięcie wskaźnika obiektu z listy. Ponosisz odpowiedzialność za usunięcie samych obiektów.

Musisz się upewnić, że wartość pozycji reprezentuje prawidłową pozycję na liście. Jeśli jest nieprawidłowa, wersja debugowana biblioteka MFC potwierdzenia.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObList::RemoveAt`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void RemoveAt (** *pozycja* położenia **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void RemoveAt (** *pozycja* położenia **);**|

### <a name="example"></a>Przykład

  Należy zachować ostrożność podczas usuwania elementu podczas iteracji listy. Poniższy przykład przedstawia technikę usuwania, która gwarantuje prawidłową wartość **pozycji** dla [GetNext](#getnext).

Aby uzyskać listę klasy `CAge`, zobacz [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#106](../../mfc/codesnippet/cpp/coblist-class_18.cpp)]

Wyniki z tego programu są następujące:

`RemoveAt example: A CObList with 2 elements`

`a CAge at $4C1E 65`

`a CAge at $4B22 21`

##  <a name="removehead"></a>CObList::RemoveHead

Usuwa element z nagłówka listy i zwraca do niego wskaźnik.

```
CObject* RemoveHead();
```

### <a name="return-value"></a>Wartość zwracana

`CObject` wskaźnik wcześniej na początku listy.

### <a name="remarks"></a>Uwagi

Przed wywołaniem `RemoveHead`należy upewnić się, że lista nie jest pusta. Jeśli lista jest pusta, wówczas wersja do debugowania biblioteka MFC potwierdzenia. Użyj [IsEmpty](#isempty) , aby sprawdzić, czy lista zawiera elementy.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObList::RemoveHead`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveHead ();**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CString RemoveHead ();**|

### <a name="example"></a>Przykład

Aby uzyskać listę klasy `CAge`, zobacz [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#107](../../mfc/codesnippet/cpp/coblist-class_19.cpp)]

##  <a name="removetail"></a>CObList::RemoveTail

Usuwa element z ogona listy i zwraca do niego wskaźnik.

```
CObject* RemoveTail();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu, który znajduje się na końcu listy.

### <a name="remarks"></a>Uwagi

Przed wywołaniem `RemoveTail`należy upewnić się, że lista nie jest pusta. Jeśli lista jest pusta, wówczas wersja do debugowania biblioteka MFC potwierdzenia. Użyj [IsEmpty](#isempty) , aby sprawdzić, czy lista zawiera elementy.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObList::RemoveTail`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveTail ();**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CString RemoveTail ();**|

### <a name="example"></a>Przykład

Aby uzyskać listę klasy `CAge`, zobacz [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#108](../../mfc/codesnippet/cpp/coblist-class_20.cpp)]

##  <a name="setat"></a>CObList::SetAt

Ustawia element w danym położeniu.

```
void SetAt(
    POSITION pos,
    CObject* newElement);
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Pozycja elementu, który ma zostać ustawiony.

*newElement*<br/>
`CObject` wskaźnik, który ma zostać zapisany na liście.

### <a name="remarks"></a>Uwagi

Zmienna typu pozycja jest kluczem dla listy. Nie jest taki sam jak indeks i nie można wykonać operacji na wartości pozycji samodzielnie. `SetAt` zapisuje wskaźnik `CObject` do określonej pozycji na liście.

Musisz się upewnić, że wartość pozycji reprezentuje prawidłową pozycję na liście. Jeśli jest nieprawidłowa, wersja debugowana biblioteka MFC potwierdzenia.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObList::SetAt`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void SetAt (pozycja** `pos` **, const CString &** `newElement` **).**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void SetAt (pozycja** `pos` **, LPCTSTR** `newElement` **);**|

### <a name="example"></a>Przykład

  Aby uzyskać listę klasy `CAge`, zobacz [CObList:: CObList](#coblist) .

[!code-cpp[NVC_MFCCollections#109](../../mfc/codesnippet/cpp/coblist-class_21.cpp)]

Wyniki z tego programu są następujące:

```Output
SetAt example: A CObList with 2 elements
a CAge at $4D98 40
a CAge at $4DB8 65
```

## <a name="see-also"></a>Zobacz także

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CStringList](../../mfc/reference/cstringlist-class.md)<br/>
[Klasa CPtrList](../../mfc/reference/cptrlist-class.md)
