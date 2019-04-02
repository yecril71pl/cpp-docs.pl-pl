---
title: Carray — klasa
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
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58779849"
---
# <a name="carray-class"></a>Carray — klasa

Obsługuje tablice, które przypominają tablice języka C, ale można dynamicznie zmniejszać i powiększać w razie.

## <a name="syntax"></a>Składnia

```
template <class TYPE, class ARG_TYPE = const TYPE&>
class CArray : public CObject
```

#### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu, który określa typ obiektów przechowywanych w tablicy. *Typ* jest parametrem, który jest zwracany przez `CArray`.

*ARG_TYPE*<br/>
Parametr szablonu, który określa typ argumentu, który umożliwia dostęp do obiektów przechowywanych w tablicy. Często odwołanie do *typu*. *ARG_TYPE* jest parametrem, który jest przekazywany do `CArray`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CArray::CArray](#carray)|Tworzy pustą tablicę.|

### <a name="public-methods"></a>Metody publiczne

|Name|Opis|
|----------|-----------------|
|[CArray::Add](#add)|Dodaje element do końca tablicy; zwiększa rozmiar tablicy, jeśli to konieczne.|
|[CArray::Append](#append)|Dołącza innej tablicy do tablicy; powiększa się tablica, jeśli to konieczne|
|[CArray::Copy](#copy)|Kopiuje innej tablicy do tablicy; zwiększa rozmiar tablicy, jeśli to konieczne.|
|[CArray::ElementAt](#elementat)|Zwraca tymczasowe odwołanie do wskaźnika elementu w tablicy.|
|[CArray::FreeExtra](#freeextra)|Zwalnia wszystkie nieużywanej pamięci powyżej bieżącego górną granicę.|
|[CArray::GetAt](#getat)|Zwraca wartość pod danym indeksem.|
|[CArray::GetCount](#getcount)|Pobiera liczbę elementów w tej tablicy.|
|[CArray::GetData](#getdata)|Umożliwia dostęp do elementów w tablicy. Może mieć wartości NULL.|
|[CArray::GetSize](#getsize)|Pobiera liczbę elementów w tej tablicy.|
|[CArray::GetUpperBound](#getupperbound)|Zwraca największy nieprawidłowy indeks.|
|[CArray::InsertAt](#insertat)|Wstawia element (lub wszystkie elementy w innej tablicy) z określonym indeksem.|
|[CArray::IsEmpty](#isempty)|Określa, czy tablica jest pusta.|
|[CArray::RemoveAll](#removeall)|Usuwa wszystkie elementy z tej tablicy.|
|[CArray::RemoveAt](#removeat)|Usuwa element pod określonym indeksem.|
|[CArray::SetAt](#setat)|Ustawia wartość dla podanego indeksu; Tablica nie może wzrosnąć.|
|[CArray::SetAtGrow](#setatgrow)|Ustawia wartość dla podanego indeksu; zwiększa rozmiar tablicy, jeśli to konieczne.|
|[CArray::SetSize](#setsize)|Ustawia liczbę elementów, które mają być zawarte w tej tablicy.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[operator&#91;&#93;](#operator_at)|Ustawia lub pobiera element pod określonym indeksem.|

## <a name="remarks"></a>Uwagi

Indeksy tablicy zawsze rozpoczynają się od pozycji 0. Możesz zdecydować, czy rozwiązać górną granicę, lub włączyć tablicy rozwinąć po dodaniu elementów poza bieżącą powiązany. Pamięć jest alokowana ciągłym górnej granicy, nawet jeśli niektóre elementy mają wartość null.

> [!NOTE]
>  Większość metod, których rozmiar `CArray` obiektu lub dodać elementy do niego użyć [memcpy_s —](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md) można przenosić elementy. Jest to problem, ponieważ `memcpy_s` nie jest zgodny z wszystkie obiekty, które wymagają Konstruktor, który ma zostać wywołana. Jeśli elementy w `CArray` nie są zgodne z `memcpy_s`, należy utworzyć nowy `CArray` odpowiedniego rozmiaru. Następnie należy użyć [CArray::Copy](#copy) i [CArray::SetAt](#setat) do wypełniania nowej tablicy, ponieważ te metody używają operatora przypisania, zamiast `memcpy_s`.

Podobnie jak w przypadku tablicy C, czas dostępu dla `CArray` indeksowanego elementu jest stała i nie zależy od rozmiaru tablicy.

> [!TIP]
>  Przed rozpoczęciem korzystania z tablicy, należy użyć [SetSize](#setsize) jej rozmiaru i przydzielanie pamięci dla niego. Jeśli nie używasz `SetSize`, dodawanie elementów do tablicy powoduje, że często ponownie przydzielane i skopiować. Częste ponowne przydzielenie kopiowania są nieefektywne i może fragmentu pamięci.

Jeśli potrzebujesz zrzut poszczególnych elementów w tablicy, należy ustawić głębokość [CDumpContext](../../mfc/reference/cdumpcontext-class.md) obiektu do 1 lub większa.

Niektóre funkcje Członkowskie to wywołanie klasy, funkcje globalne pomocy, które muszą być dostosowane dla większości zastosowań `CArray` klasy. Zobacz temat [pomocnicy klasy kolekcji](../../mfc/reference/collection-class-helpers.md) w sekcji makr MFC i funkcje globalne.

Wyprowadzanie klasy tablicy przypomina tworzenie wartości pochodnych z listy.

Aby uzyskać więcej informacji o sposobie używania `CArray`, zapoznaj się z artykułem [kolekcje](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CArray`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtempl.h

##  <a name="add"></a>  CArray::Add

Dodaje nowy element do końca tablicy, rośnie tablicy o 1.

```
INT_PTR Add(ARG_TYPE newElement);
```

### <a name="parameters"></a>Parametry

*ARG_TYPE*<br/>
Parametr szablonu określający typ argumentów odwoływania się do elementów w tej tablicy.

*newElement*<br/>
Element, który ma zostać dodany do tej tablicy.

### <a name="return-value"></a>Wartość zwracana

Indeks dodanego elementu.

### <a name="remarks"></a>Uwagi

Jeśli [SetSize](#setsize) został użyty z `nGrowBy` wartość większą niż 1, a następnie dodatkową pamięć, które mogą być przydzielone. Jednakże górna granica wzrosną tylko 1.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#22](../../mfc/codesnippet/cpp/carray-class_1.cpp)]

##  <a name="append"></a>  CArray::Append

Wywołaj tę funkcję elementu członkowskiego, aby dodać zawartość jednej tablicy do końca innej.

```
INT_PTR Append(const CArray& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
Źródło elementów, które mają być dołączane do tablicy.

### <a name="return-value"></a>Wartość zwracana

Indeks pierwszy dołączony element.

### <a name="remarks"></a>Uwagi

Tablice muszą być tego samego typu.

Jeśli to konieczne, `Append` może przydzielić dodatkową pamięć, aby pomieścić elementów do tablicy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#23](../../mfc/codesnippet/cpp/carray-class_2.cpp)]

##  <a name="carray"></a>  CArray::CArray

Tworzy pustą tablicę.

```
CArray();
```

### <a name="remarks"></a>Uwagi

Tablica rośnie jeden element w danym momencie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#24](../../mfc/codesnippet/cpp/carray-class_3.cpp)]

##  <a name="copy"></a>  CArray::Copy

Użyj tej funkcji elementu członkowskiego, aby skopiować elementy tablicy do innego.

```
void Copy(const CArray& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
Źródło elementów, które mają być kopiowane do tablicy.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję elementu członkowskiego w celu zastąpienia elementów tablicy elementów innej tablicy.

`Copy` nie spowoduje zwolnienia pamięci. Jednakże, jeśli to konieczne, `Copy` może przydzielić dodatkową pamięć, aby pomieścić elementów kopiowanych z tablicą.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#25](../../mfc/codesnippet/cpp/carray-class_4.cpp)]

##  <a name="elementat"></a>  CArray::ElementAt

Zwraca tymczasowe odwołanie do określonego elementu w tablicy.

```
TYPE& ElementAt(INT_PTR nIndex);
const TYPE& ElementAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Liczba całkowita indeksu, który jest większa lub równa 0 i mniejsza niż wartość zwrócona przez obiekt [GetUpperBound](#getupperbound).

### <a name="return-value"></a>Wartość zwracana

Odwołanie do elementu tablicy.

### <a name="remarks"></a>Uwagi

Służy do implementowania operatora przypisania po lewej stronie macierzy.

### <a name="example"></a>Przykład

  Zobacz przykład [getsize —](#getsize).

##  <a name="freeextra"></a>  CArray::FreeExtra

Zwalnia dodatkową pamięć, która została przydzielona podczas został wzrosła tablicy.

```
void FreeExtra();
```

### <a name="remarks"></a>Uwagi

Ta funkcja nie ma wpływu na rozmiar lub górna granica tablicy.

### <a name="example"></a>Przykład

  Zobacz przykład [GetData](#getdata).

##  <a name="getat"></a>  CArray::GetAt

Zwraca element tablicy o określonym indeksie.

```
TYPE& GetAt(INT_PTR nIndex);
const TYPE& GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów tablicy.

*nIndex*<br/>
Liczba całkowita indeksu, który jest większa lub równa 0 i mniejsza niż wartość zwrócona przez obiekt [GetUpperBound](#getupperbound).

### <a name="return-value"></a>Wartość zwracana

Element tablicy, która obecnie pod tym indeksem.

### <a name="remarks"></a>Uwagi

Przekazywanie wartości ujemnej lub wartość większa niż wartość zwrócona przez obiekt `GetUpperBound` spowoduje niepowodzenie asercji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#26](../../mfc/codesnippet/cpp/carray-class_5.cpp)]

##  <a name="getcount"></a>  CArray::GetCount

Zwraca liczbę elementów tablicy.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w tablicy.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby pobrać liczbę elementów w tablicy. Ponieważ indeksy są od zera, rozmiar jest większy od największego indeksu 1. Wywołanie tej metody spowoduje wygenerowanie ten sam wynik jako [CArray::GetSize](#getsize) metody.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#27](../../mfc/codesnippet/cpp/carray-class_6.cpp)]

##  <a name="getdata"></a>  CArray::GetData

Użyj tej funkcji elementu członkowskiego do uzyskania bezpośredniego dostępu do elementów w tablicy.

```
const TYPE* GetData() const;
TYPE* GetData();
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów tablicy.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do elementu tablicy.

### <a name="remarks"></a>Uwagi

Jeśli żadne elementy są dostępne, `GetData` zwraca wartość null.

Gdy bezpośredni dostęp do elementów tablicy pomoże szybciej, należy zachować ostrożność podczas wywoływania `GetData`; wszelkie błędy wprowadzone bezpośrednio wpływają na elementy tablicy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#28](../../mfc/codesnippet/cpp/carray-class_7.cpp)]

##  <a name="getsize"></a>  CArray::GetSize

Zwraca rozmiar tablicy.

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>Uwagi

Ponieważ indeksy są od zera, rozmiar jest większy od największego indeksu 1. Wywołanie tej metody spowoduje wygenerowanie ten sam wynik jako [CArray::GetCount](#getcount) metody.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#29](../../mfc/codesnippet/cpp/carray-class_8.cpp)]

##  <a name="getupperbound"></a>  CArray::GetUpperBound

Zwraca bieżący górną granicę tej tablicy.

```
INT_PTR GetUpperBound() const;
```

### <a name="remarks"></a>Uwagi

Ponieważ indeksy tablicy zaczynają się od zera, ta funkcja zwraca wartość 1 poniżej `GetSize`.

Warunek `GetUpperBound( )` = -1 oznacza, że tablica nie zawiera żadnych elementów.

### <a name="example"></a>Przykład

  Zobacz przykład [CArray::GetAt](#getat).

##  <a name="insertat"></a>  CArray::InsertAt

Pierwsza wersja `InsertAt` wstawia jednego elementu (lub wiele kopii elementu) od określonego indeksu tablicy.

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
Liczba całkowita indeksu, który może być większa niż wartość zwrócona przez obiekt `GetUpperBound`.

*ARG_TYPE*<br/>
Parametr szablonu określający typ elementów w tej tablicy.

*newElement*<br/>
Element, który ma być umieszczone w tej tablicy.

*nCount*<br/>
Liczba przypadków, gdy ten element powinien być wstawiany (wartość domyślna to 1).

*nStartIndex*<br/>
Liczba całkowita indeksu, który może być większa niż wartość zwrócona przez obiekt [GetUpperBound](#getupperbound).

*pNewArray*<br/>
Innej tablicy, która zawiera elementy, które mają zostać dodane do tej tablicy.

### <a name="remarks"></a>Uwagi

W procesie przenosi (przez zwiększanie indeks) istniejącego elementu w ten indeks, a przewiduje się wszystkie elementy, nad nim.

Druga wersja wstawia wszystkie elementy z innego `CArray` kolekcji, zaczynając od *nStartIndex* pozycji.

`SetAt` Funkcji, z kolei zastępuje jeden element określonej tablicy i nie przesunięcia żadnych elementów.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#30](../../mfc/codesnippet/cpp/carray-class_9.cpp)]

##  <a name="isempty"></a>  CArray::IsEmpty

Określa, czy tablica jest pusta.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli tablica nie zawiera elementów; w przeciwnym razie 0.

##  <a name="operator_at"></a>  CArray::operator \[\]

Tych operatorów indeksu dolnego są wygodnym zastępuje [SetAt](#setat) i [GetAt](#getat) funkcji.

```
TYPE& operator[](int_ptr nindex);
const TYPE& operator[](int_ptr nindex) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów w tej tablicy.

*nIndex*<br/>
Indeks elementu, można uzyskać dostęp.

### <a name="remarks"></a>Uwagi

Pierwszy operator wywoływane dla tablic, które nie są **const**, mogą być używane w prawo (r) lub (l wartość) po lewej stronie instrukcji przypisania. Druga Strona, wywołana dla **const** tablic, mogą być używane tylko po prawej stronie.

Wersja do debugowania biblioteki potwierdza, jeśli indeksu dolnego (albo po lewej lub prawej stronie instrukcji przypisania) jest poza zakresem.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#34](../../mfc/codesnippet/cpp/carray-class_10.cpp)]

##  <a name="relocateelements"></a>  CArray::RelocateElements

Przenosi dane do nowego buforu, gdy tablicy należy zwiększać i zmniejszać.

```
template<class TYPE, class ARG_TYPE>
AFX_INLINE void CArray<TYPE, ARG_TYPE>::RelocateElements(
    TYPE* pNewData,
    const TYPE* pData,
    INT_PTR nCount);
```

### <a name="parameters"></a>Parametry

*pNewData*<br/>
Bufor nowego tablicy elementów.

*pData*<br/>
Stary tablicę elementów.

*nCount*<br/>
Liczba elementów w tablicy stary.

### <a name="remarks"></a>Uwagi

*pNewData* zawsze jest wystarczająco duży, aby pomieścić wszystkie *pData* elementów.

[CArray](../../mfc/reference/carray-class.md) implementacja używa tej metody można skopiować do bufor nowego stare dane, gdy tablicy należy zwiększać i zmniejszać (gdy [SetSize](#setsize) lub [FreeExtra](#freeextra) są nazywane). Domyślna implementacja kopiuje tylko dane.

Dla tablic, w których element zawiera wskaźnik do jednego ze swoich własnych członków lub inną strukturę zawiera wskaźnik do jednego z elementów tablicy wskaźniki nie są aktualizowane w zwykłych kopii. W tym przypadku można poprawić wskaźniki, implementując specjalizacją `RelocateElements` przy użyciu odpowiednich typów. Ponosisz odpowiedzialność do kopiowania danych.

##  <a name="removeall"></a>  CArray::RemoveAll

Usuwa wszystkie elementy z tej tablicy.

```
void RemoveAll();
```

### <a name="remarks"></a>Uwagi

Jeśli tablica jest pusty, funkcja jest nadal działa.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#31](../../mfc/codesnippet/cpp/carray-class_11.cpp)]

##  <a name="removeat"></a>  CArray::RemoveAt

Usuwa jeden lub więcej elementów, zaczynając od określonego indeksu tablicy.

```
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Liczba całkowita indeksu, który jest większa lub równa 0 i mniejsza niż wartość zwrócona przez obiekt [GetUpperBound](#getupperbound).

*nCount*<br/>
Liczba elementów do usunięcia.

### <a name="remarks"></a>Uwagi

W procesie jego przenosi w dół wszystkie elementy powyżej usunięto następującą liczbę elementów. Jego zmniejsza górnej granicy tablicy, ale nie spowoduje zwolnienia pamięci.

Jeśli próbujesz usunąć więcej elementów niż znajdują się w tablicy powyżej punktu usunięcie wersji do debugowania biblioteki potwierdzenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#32](../../mfc/codesnippet/cpp/carray-class_12.cpp)]

##  <a name="setat"></a>  CArray::SetAt

Ustawia element tablicy o określonym indeksie.

```
void SetAt(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Liczba całkowita indeksu, który jest większa lub równa 0 i mniejsza niż wartość zwrócona przez obiekt [GetUpperBound](#getupperbound).

*ARG_TYPE*<br/>
Parametr szablonu określający typ argumenty używane do odwoływania się do elementów tablicy.

*newElement*<br/>
Nowa wartość elementu mają być przechowywane w określonej pozycji.

### <a name="remarks"></a>Uwagi

`SetAt` nie spowoduje, że tablica rośnie. Użyj [SetAtGrow](#setatgrow) chcącym tablicy rośnie automatycznie.

Należy się upewnić, że wartość indeksu reprezentuje poprawnej pozycji w tablicy. Jeśli jest poza zakresem, wersja do debugowania biblioteki potwierdzenia.

### <a name="example"></a>Przykład

  Zobacz przykład [GetAt](#getat).

##  <a name="setatgrow"></a>  CArray::SetAtGrow

Ustawia element tablicy o określonym indeksie.

```
void SetAtGrow(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks liczby całkowitej, która jest większa lub równa 0.

*ARG_TYPE*<br/>
Parametr szablonu określający typ elementów w tablicy.

*newElement*<br/>
Element, który ma zostać dodany do tej tablicy. Wartość NULL jest dozwolona.

### <a name="remarks"></a>Uwagi

Tablica powiększa się automatycznie, jeśli to konieczne (górna granica jest dostosowane, aby pomieścić nowy element).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#33](../../mfc/codesnippet/cpp/carray-class_13.cpp)]

##  <a name="setsize"></a>  CArray::SetSize

Określa rozmiar tablicy pustego lub istniejącego; przydziela pamięć, jeśli to konieczne.

```
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>Parametry

*nNewSize*<br/>
Nowy rozmiar tablicy (liczba elementów). Musi być większa lub równa 0.

*nGrowBy*<br/>
Minimalna liczba gniazd element do przydzielenia, jeśli konieczne jest zwiększenie rozmiaru.

### <a name="remarks"></a>Uwagi

Jeśli nowy rozmiar jest mniejszy niż stary rozmiar, tablica jest skracana i zwolnieniu wszystkich nieużywanej pamięci.

Ta funkcja służy do ustawiania rozmiaru tablicy, przed rozpoczęciem korzystania z tablicy. Jeśli nie używasz `SetSize`, dodawanie elementów do tablicy powoduje, że często ponownie przydzielane i skopiować. Częste ponowne przydzielenie kopiowania są nieefektywne i może fragmentu pamięci.

*NGrowBy* parametru wpływa na alokacji pamięci wewnętrznej, podczas gdy rośnie tablicy. Jego użycie nigdy nie wpływa na rozmiar tablicy zgłoszonej przez [getsize —](#getsize) i [GetUpperBound](#getupperbound). Jeśli używana jest wartość domyślna, MFC przydziela pamięci w sposób obliczane, aby uniknąć fragmentacji pamięci i zoptymalizować wydajność w większości przypadków.

### <a name="example"></a>Przykład

  Zobacz przykład [GetData](#getdata).

## <a name="see-also"></a>Zobacz także

[Próbki MFC ZBIERANIE](../../overview/visual-cpp-samples.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CObArray](../../mfc/reference/cobarray-class.md)<br/>
[Pomocnicy klasy kolekcji](../../mfc/reference/collection-class-helpers.md)
