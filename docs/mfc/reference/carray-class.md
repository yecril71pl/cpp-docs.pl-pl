---
title: Klasa CArray
ms.date: 11/04/2016
f1_keywords:
- CArray
- AFXTEMPL/CArray
- AFXTEMPL/CArray::CArray
- AFXTEMPL/CArray::Add
- AFXTEMPL/CArray::Append
- AFXTEMPL/CArray::Copy
- AFXTEMPL/CArray::ElementAt
- AFXTEMPL/CArray::FreeExtra
- AFXTEMPL/CArray::GetAt
- AFXTEMPL/CArray::GetCount
- AFXTEMPL/CArray::GetData
- AFXTEMPL/CArray::GetSize
- AFXTEMPL/CArray::GetUpperBound
- AFXTEMPL/CArray::InsertAt
- AFXTEMPL/CArray::IsEmpty
- AFXTEMPL/CArray::RemoveAll
- AFXTEMPL/CArray::RemoveAt
- AFXTEMPL/CArray::SetAt
- AFXTEMPL/CArray::SetAtGrow
- AFXTEMPL/CArray::SetSize
helpviewer_keywords:
- CArray [MFC], CArray
- CArray [MFC], Add
- CArray [MFC], Append
- CArray [MFC], Copy
- CArray [MFC], ElementAt
- CArray [MFC], FreeExtra
- CArray [MFC], GetAt
- CArray [MFC], GetCount
- CArray [MFC], GetData
- CArray [MFC], GetSize
- CArray [MFC], GetUpperBound
- CArray [MFC], InsertAt
- CArray [MFC], IsEmpty
- CArray [MFC], RemoveAll
- CArray [MFC], RemoveAt
- CArray [MFC], SetAt
- CArray [MFC], SetAtGrow
- CArray [MFC], SetSize
ms.assetid: fead8b00-4cfd-4625-ad0e-251df62ba92f
ms.openlocfilehash: f82dbf7dce2e14bf760bb76d23d23f667797ee0f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418861"
---
# <a name="carray-class"></a>Klasa CArray

Obsługuje tablice, które są podobne do tablic języka C, ale mogą dynamicznie zmniejszać i zwiększać się w miarę potrzeb.

## <a name="syntax"></a>Składnia

```
template <class TYPE, class ARG_TYPE = const TYPE&>
class CArray : public CObject
```

#### <a name="parameters"></a>Parametry

*Wprowadź*<br/>
Parametr szablonu, który określa typ obiektów przechowywanych w tablicy. *Typ* jest parametrem zwracanym przez `CArray`.

*ARG_TYPE*<br/>
Parametr szablonu, który określa typ argumentu, który jest używany do uzyskiwania dostępu do obiektów przechowywanych w tablicy. Często odwołanie do *typu*. *ARG_TYPE* jest parametrem, który jest przesyłany do `CArray`.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CArray::CArray](#carray)|Konstruuje pustą tablicę.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CArray:: Add](#add)|Dodaje element na końcu tablicy; w razie potrzeby powiększa tablicę.|
|[CArray:: Append](#append)|Dołącza kolejną tablicę do tablicy; powiększa tablicę w razie potrzeby|
|[CArray:: Copy](#copy)|Kopiuje kolejną tablicę do tablicy; w razie potrzeby powiększa tablicę.|
|[CArray::ElementAt](#elementat)|Zwraca tymczasowe odwołanie do wskaźnika elementu w tablicy.|
|[CArray::FreeExtra](#freeextra)|Zwalnia wszystkie nieużywane pamięci powyżej bieżącej górnej granicy.|
|[CArray::GetAt](#getat)|Zwraca wartość w danym indeksie.|
|[CArray:: GetCount](#getcount)|Pobiera liczbę elementów w tej tablicy.|
|[CArray:: GetData](#getdata)|Umożliwia dostęp do elementów w tablicy. Może mieć wartość NULL.|
|[CArray:: GetSize](#getsize)|Pobiera liczbę elementów w tej tablicy.|
|[CArray::GetUpperBound](#getupperbound)|Zwraca największy prawidłowy indeks.|
|[CArray::InsertAt](#insertat)|Wstawia element (lub wszystkie elementy w innej tablicy) o określonym indeksie.|
|[CArray:: IsEmpty](#isempty)|Określa, czy tablica jest pusta.|
|[CArray::](#removeall)|Usuwa wszystkie elementy z tej tablicy.|
|[CArray::RemoveAt](#removeat)|Usuwa element z określonym indeksem.|
|[CArray::SetAt](#setat)|Ustawia wartość dla danego indeksu; Tablica nie może być większa.|
|[CArray::SetAtGrow](#setatgrow)|Ustawia wartość dla danego indeksu; w razie potrzeby powiększa tablicę.|
|[CArray:: setSize](#setsize)|Ustawia liczbę elementów, które mają być zawarte w tej tablicy.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[zakład&#91;&#93;](#operator_at)|Ustawia lub pobiera element pod określonym indeksem.|

## <a name="remarks"></a>Uwagi

Indeksy tablicy zawsze zaczynają się na pozycji 0. Można zdecydować, czy naprawić górną granicę, czy włączyć rozszerzanie tablicy po dodaniu elementów poza bieżącą granicą. Pamięć jest przydzielono w sposób ciągły do górnej granicy, nawet jeśli niektóre elementy mają wartość null.

> [!NOTE]
>  Większość metod, które umożliwiają zmianę rozmiaru obiektu `CArray` lub dodanie elementów do [memcpy_s](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md) , aby przenieść elementy. Jest to problem, ponieważ `memcpy_s` nie jest zgodny z żadnym obiektem, który wymaga wywołania konstruktora. Jeśli elementy w `CArray` nie są zgodne z `memcpy_s`, należy utworzyć nowy `CArray` o odpowiednim rozmiarze. Następnie należy użyć [CArray:: Copy](#copy) i [CArray:: SetAt](#setat) , aby wypełnić nową tablicę, ponieważ te metody używają operatora przypisania zamiast `memcpy_s`.

Podobnie jak w przypadku tablicy języka C, czas dostępu dla `CArray` indeksowanego elementu jest stały i jest niezależny od rozmiaru tablicy.

> [!TIP]
>  Przed użyciem tablicy Użyj polecenia [SetSize](#setsize) , aby określić rozmiar i przydzielić pamięć dla tego obiektu. Jeśli nie używasz `SetSize`, dodawanie elementów do tablicy powoduje częste ponowną alokację i kopiowanie. Częste ponowne przydzielanie i kopiowanie są niewydajne i mogą fragmentację pamięci.

Jeśli potrzebujesz zrzutu poszczególnych elementów w tablicy, musisz ustawić głębokość obiektu [CDumpContext](../../mfc/reference/cdumpcontext-class.md) na 1 lub większą.

Niektóre funkcje członkowskie tej klasy wywołują globalne funkcje pomocnika, które muszą być dostosowane do większości celów klasy `CArray`. Zobacz [pomocników klasy kolekcji](../../mfc/reference/collection-class-helpers.md) tematów w makrze MFC i w sekcji Globals.

Klasa pochodna klasy Array jest taka sama jak pochodna listy.

Więcej informacji o sposobach korzystania z `CArray`można znaleźć w artykułach [kolekcje](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CArray`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtempl. h

##  <a name="add"></a>CArray:: Add

Dodaje nowy element na końcu tablicy, zwiększając tablicę o 1.

```
INT_PTR Add(ARG_TYPE newElement);
```

### <a name="parameters"></a>Parametry

*ARG_TYPE*<br/>
Parametr szablonu określający typ argumentów odwołujących się do elementów w tej tablicy.

*newElement*<br/>
Element, który ma zostać dodany do tej tablicy.

### <a name="return-value"></a>Wartość zwrócona

Indeks dodanego elementu.

### <a name="remarks"></a>Uwagi

Jeśli wartość [SetSize](#setsize) została użyta z wartością `nGrowBy` większą niż 1, może być przydzielono dodatkową pamięć. Górna granica zostanie jednak zwiększona o 1.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#22](../../mfc/codesnippet/cpp/carray-class_1.cpp)]

##  <a name="append"></a>CArray:: Append

Wywołaj tę funkcję elementu członkowskiego, aby dodać zawartość jednej tablicy do końca innej.

```
INT_PTR Append(const CArray& src);
```

### <a name="parameters"></a>Parametry

*SRC*<br/>
Źródło elementów do dołączenia do tablicy.

### <a name="return-value"></a>Wartość zwrócona

Indeks pierwszego dołączonego elementu.

### <a name="remarks"></a>Uwagi

Tablice muszą być tego samego typu.

W razie potrzeby `Append` może przydzielić dodatkową pamięć, aby pomieścić elementy dołączone do tablicy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#23](../../mfc/codesnippet/cpp/carray-class_2.cpp)]

##  <a name="carray"></a>CArray::CArray

Konstruuje pustą tablicę.

```
CArray();
```

### <a name="remarks"></a>Uwagi

Tablica powiększa jeden element jednocześnie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#24](../../mfc/codesnippet/cpp/carray-class_3.cpp)]

##  <a name="copy"></a>CArray:: Copy

Użyj tej funkcji elementu członkowskiego, aby skopiować elementy jednej tablicy do innej.

```
void Copy(const CArray& src);
```

### <a name="parameters"></a>Parametry

*SRC*<br/>
Źródło elementów, które mają być skopiowane do tablicy.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję elementu członkowskiego, aby zastąpić elementy jednej tablicy elementami innej tablicy.

`Copy` nie zwalnia pamięci; Jednak w razie potrzeby `Copy` może przydzielić dodatkową pamięć, aby pomieścić elementy skopiowane do tablicy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#25](../../mfc/codesnippet/cpp/carray-class_4.cpp)]

##  <a name="elementat"></a>CArray::ElementAt

Zwraca tymczasowe odwołanie do określonego elementu w tablicy.

```
TYPE& ElementAt(INT_PTR nIndex);
const TYPE& ElementAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks liczby całkowitej, który jest większy lub równy 0 i mniejszy lub równy wartości zwracanej przez [GetUpperBound](#getupperbound).

### <a name="return-value"></a>Wartość zwrócona

Odwołanie do elementu tablicy.

### <a name="remarks"></a>Uwagi

Służy do implementacji operatora przypisania lewej strony dla tablic.

### <a name="example"></a>Przykład

  Zobacz przykład dla elementu [GetSize](#getsize).

##  <a name="freeextra"></a>CArray::FreeExtra

Zwalnia wszelkie dodatkowe pamięci, które zostały przydzieloną podczas uprawy tablicy.

```
void FreeExtra();
```

### <a name="remarks"></a>Uwagi

Ta funkcja nie ma wpływu na rozmiar ani górną granicę tablicy.

### <a name="example"></a>Przykład

  Zobacz przykład dla elementu [GetData](#getdata).

##  <a name="getat"></a>CArray::GetAt

Zwraca element array o określonym indeksie.

```
TYPE& GetAt(INT_PTR nIndex);
const TYPE& GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parametry

*Wprowadź*<br/>
Parametr szablonu określający typ elementów tablicy.

*nIndex*<br/>
Indeks liczby całkowitej, który jest większy lub równy 0 i mniejszy lub równy wartości zwracanej przez [GetUpperBound](#getupperbound).

### <a name="return-value"></a>Wartość zwrócona

Element tablicy w bieżącym indeksie.

### <a name="remarks"></a>Uwagi

Przekazanie wartości ujemnej lub wartości większej niż wartość zwrócona przez `GetUpperBound` spowoduje niepowodzenie potwierdzenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#26](../../mfc/codesnippet/cpp/carray-class_5.cpp)]

##  <a name="getcount"></a>CArray:: GetCount

Zwraca liczbę elementów tablicy.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Wartość zwrócona

Liczba elementów w tablicy.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby pobrać liczbę elementów w tablicy. Ponieważ indeksy są oparte na zero, rozmiar jest większy niż największy indeks. Wywołanie tej metody spowoduje wygenerowanie tego samego wyniku co Metoda [CArray:: GetSize](#getsize) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#27](../../mfc/codesnippet/cpp/carray-class_6.cpp)]

##  <a name="getdata"></a>CArray:: GetData

Użyj tej funkcji elementu członkowskiego, aby uzyskać bezpośredni dostęp do elementów w tablicy.

```
const TYPE* GetData() const;
TYPE* GetData();
```

### <a name="parameters"></a>Parametry

*Wprowadź*<br/>
Parametr szablonu określający typ elementów tablicy.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do elementu tablicy.

### <a name="remarks"></a>Uwagi

Jeśli żadne elementy nie są dostępne, `GetData` zwraca wartość null.

Mimo że bezpośredni dostęp do elementów tablicy może ułatwić szybkie działanie, należy zachować ostrożność podczas wywoływania `GetData`; wszystkie błędy wprowadzane bezpośrednio mają wpływ na elementy tablicy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#28](../../mfc/codesnippet/cpp/carray-class_7.cpp)]

##  <a name="getsize"></a>CArray:: GetSize

Zwraca rozmiar tablicy.

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>Uwagi

Ponieważ indeksy są oparte na zero, rozmiar jest większy niż największy indeks. Wywołanie tej metody spowoduje wygenerowanie tego samego wyniku co Metoda [CArray:: GetCount](#getcount) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#29](../../mfc/codesnippet/cpp/carray-class_8.cpp)]

##  <a name="getupperbound"></a>CArray::GetUpperBound

Zwraca bieżącą górną granicę tej tablicy.

```
INT_PTR GetUpperBound() const;
```

### <a name="remarks"></a>Uwagi

Ponieważ indeksy tablicy są oparte na zero, ta funkcja zwraca wartość 1 mniejszą niż `GetSize`.

Warunek `GetUpperBound( )` =-1 wskazuje, że tablica nie zawiera żadnych elementów.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CArray:: GetAt](#getat).

##  <a name="insertat"></a>CArray::InsertAt

Pierwsza wersja `InsertAt` Wstawia jeden element (lub wiele kopii elementu) o określonym indeksie w tablicy.

```
void InsertAt(
    INT_PTR nIndex,
    ARG_TYPE newElement,
    INT_PTR nCount = 1);

void InsertAt(
    INT_PTR nStartIndex,
    CArray* pNewArray);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks liczby całkowitej, który może być większy niż wartość zwrócona przez `GetUpperBound`.

*ARG_TYPE*<br/>
Parametr szablonu określający typ elementów w tej tablicy.

*newElement*<br/>
Element, który ma zostać umieszczony w tej tablicy.

*nCount*<br/>
Liczba przypadków wstawienia tego elementu (wartość domyślna to 1).

*nStartIndex*<br/>
Indeks liczby całkowitej, który może być większy niż wartość zwrócona przez [GetUpperBound](#getupperbound).

*pNewArray*<br/>
Inna tablica zawierająca elementy, które mają zostać dodane do tej tablicy.

### <a name="remarks"></a>Uwagi

W procesie zostaje on przesunięty w górę (przez zwiększenie indeksu) istniejący element w tym indeksie i przesunie wszystkie elementy znajdujące się powyżej.

Druga wersja wstawia wszystkie elementy z innej kolekcji `CArray`, zaczynając od pozycji *nStartIndex* .

Funkcja `SetAt`, w przeciwieństwie, zastępuje jeden określony element tablicy i nie przesuwa żadnych elementów.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#30](../../mfc/codesnippet/cpp/carray-class_9.cpp)]

##  <a name="isempty"></a>CArray:: IsEmpty

Określa, czy tablica jest pusta.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Wartość zwrócona

Różne od zera, jeśli tablica nie zawiera żadnych elementów; w przeciwnym razie 0.

##  <a name="operator_at"></a>CArray:: operator \[\]

Te operatory indeksów dolnych są wygodnym substytutem funkcji [SetAt](#setat) i [GetAt](#getat) .

```
TYPE& operator[](int_ptr nindex);
const TYPE& operator[](int_ptr nindex) const;
```

### <a name="parameters"></a>Parametry

*Wprowadź*<br/>
Parametr szablonu określający typ elementów w tej tablicy.

*nIndex*<br/>
Indeks elementu do uzyskania dostępu.

### <a name="remarks"></a>Uwagi

Pierwszy operator wywoływany dla tablic, które nie są **stałe**, może być używany po prawej stronie (r-Value) lub lewej (l-wartości) instrukcji przypisania. Sekunda, wywołana dla tablic **stałych** , może być używana tylko po prawej stronie.

Wersja debugowania biblioteki potwierdza, czy indeks dolny (w lewej lub prawej stronie instrukcji przypisania) znajduje się poza zakresem.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#34](../../mfc/codesnippet/cpp/carray-class_10.cpp)]

##  <a name="relocateelements"></a>CArray::RelocateElements

Lokalizuje dane do nowego buforu, gdy tablica powinna zostać powiększona lub pomniejsza.

```
template<class TYPE, class ARG_TYPE>
AFX_INLINE void CArray<TYPE, ARG_TYPE>::RelocateElements(
    TYPE* pNewData,
    const TYPE* pData,
    INT_PTR nCount);
```

### <a name="parameters"></a>Parametry

*pNewData*<br/>
Nowy bufor dla tablicy elementów.

*pData*<br/>
Stara Tablica elementów.

*nCount*<br/>
Liczba elementów w starej tablicy.

### <a name="remarks"></a>Uwagi

*pNewData* jest zawsze wystarczająco duże, aby pomieścić wszystkie elementy *pData* .

Implementacja [CArray](../../mfc/reference/carray-class.md) używa tej metody do kopiowania starych danych do nowego buforu, gdy tablica powinna zostać powiększana lub zmniejszana (gdy wywoływana jest funkcja [SetSize](#setsize) lub [FreeExtra](#freeextra) ). Domyślna implementacja właśnie kopiuje dane.

W przypadku tablic, w których element zawiera wskaźnik do jednego z jego elementów członkowskich lub inna struktura zawiera wskaźnik do jednego z elementów tablicy, wskaźniki nie są aktualizowane w postaci zwykłego kopiowania. W takim przypadku można poprawić wskaźniki przez implementację specjalizacji `RelocateElements` z odpowiednimi typami. Użytkownik jest również odpowiedzialny za kopiowanie danych.

##  <a name="removeall"></a>CArray::

Usuwa wszystkie elementy z tej tablicy.

```
void RemoveAll();
```

### <a name="remarks"></a>Uwagi

Jeśli tablica jest już pusta, funkcja nadal działa.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#31](../../mfc/codesnippet/cpp/carray-class_11.cpp)]

##  <a name="removeat"></a>CArray::RemoveAt

Usuwa jeden lub więcej elementów, zaczynając od określonego indeksu w tablicy.

```
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks liczby całkowitej, który jest większy lub równy 0 i mniejszy lub równy wartości zwracanej przez [GetUpperBound](#getupperbound).

*nCount*<br/>
Liczba elementów do usunięcia.

### <a name="remarks"></a>Uwagi

W procesie przesunie wszystkie elementy powyżej usuniętych elementów. Zmniejsza górną granicę tablicy, ale nie zwalnia pamięci.

Jeśli spróbujesz usunąć więcej elementów niż znajduje się w tablicy powyżej punktu usuwania, wówczas wersja do debugowania zostanie przeszukana w bibliotece.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#32](../../mfc/codesnippet/cpp/carray-class_12.cpp)]

##  <a name="setat"></a>CArray::SetAt

Ustawia element Array pod określonym indeksem.

```
void SetAt(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks liczby całkowitej, który jest większy lub równy 0 i mniejszy lub równy wartości zwracanej przez [GetUpperBound](#getupperbound).

*ARG_TYPE*<br/>
Parametr szablonu określający typ argumentów używanych do odwoływania się do elementów tablicy.

*newElement*<br/>
Wartość nowego elementu, która ma być przechowywana w określonym położeniu.

### <a name="remarks"></a>Uwagi

`SetAt` nie spowoduje wzrostu tablicy. Użyj [SetAtGrow](#setatgrow) , jeśli chcesz, aby tablica była powiększana automatycznie.

Musisz się upewnić, że wartość indeksu reprezentuje prawidłową pozycję w tablicy. Jeśli znajduje się poza zakresem, wówczas wersja do debugowania zostanie przeprowadzona.

### <a name="example"></a>Przykład

  Zobacz przykład dla [GetAt](#getat).

##  <a name="setatgrow"></a>CArray::SetAtGrow

Ustawia element Array pod określonym indeksem.

```
void SetAtGrow(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks liczby całkowitej, który jest większy lub równy 0.

*ARG_TYPE*<br/>
Parametr szablonu określający typ elementów w tablicy.

*newElement*<br/>
Element, który ma zostać dodany do tej tablicy. Dozwolona jest wartość NULL.

### <a name="remarks"></a>Uwagi

Tablica powiększa się automatycznie w razie potrzeby (to znaczy górną granicę dostosowuje się w celu uwzględnienia nowego elementu).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#33](../../mfc/codesnippet/cpp/carray-class_13.cpp)]

##  <a name="setsize"></a>CArray:: setSize

Ustala rozmiar pustej lub istniejącej tablicy; przydziela pamięć w razie potrzeby.

```
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>Parametry

*nNewSize*<br/>
Nowy rozmiar tablicy (liczba elementów). Musi być większa lub równa 0.

*nGrowBy*<br/>
Minimalna liczba gniazd elementów do przydzielenia w przypadku konieczności zwiększenia rozmiaru.

### <a name="remarks"></a>Uwagi

Jeśli nowy rozmiar jest mniejszy niż stary rozmiar, tablica zostanie obcięta, a cała niewykorzystana pamięć zostanie wydzielona.

Użyj tej funkcji, aby ustawić rozmiar tablicy przed rozpoczęciem korzystania z tablicy. Jeśli nie używasz `SetSize`, dodawanie elementów do tablicy powoduje częste ponowną alokację i kopiowanie. Częste ponowne przydzielanie i kopiowanie są niewydajne i mogą fragmentację pamięci.

Parametr *nGrowBy* ma wpływ na alokację pamięci wewnętrznej podczas wzrostu tablicy. Jego użycie nigdy nie wpływa na rozmiar tablicy w postaci zgłoszonej przez [GetSize](#getsize) i [GetUpperBound](#getupperbound). Jeśli zostanie użyta wartość domyślna, MFC przydziela pamięć w sposób obliczeniowy, aby uniknąć fragmentacji pamięci i zoptymalizować wydajność w większości przypadków.

### <a name="example"></a>Przykład

  Zobacz przykład dla elementu [GetData](#getdata).

## <a name="see-also"></a>Zobacz też

[ZBIERANIE próbek MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CObArray](../../mfc/reference/cobarray-class.md)<br/>
[Pomocnicy klasy kolekcji](../../mfc/reference/collection-class-helpers.md)
