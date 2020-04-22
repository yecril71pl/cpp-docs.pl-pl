---
title: Klasa CMap
ms.date: 11/04/2016
f1_keywords:
- CMap
- AFXTEMPL/CMap
- AFXTEMPL/CMap::CPair
- AFXTEMPL/CMap::CMap
- AFXTEMPL/CMap::GetCount
- AFXTEMPL/CMap::GetHashTableSize
- AFXTEMPL/CMap::GetNextAssoc
- AFXTEMPL/CMap::GetSize
- AFXTEMPL/CMap::GetStartPosition
- AFXTEMPL/CMap::InitHashTable
- AFXTEMPL/CMap::IsEmpty
- AFXTEMPL/CMap::Lookup
- AFXTEMPL/CMap::PGetFirstAssoc
- AFXTEMPL/CMap::PGetNextAssoc
- AFXTEMPL/CMap::PLookup
- AFXTEMPL/CMap::RemoveAll
- AFXTEMPL/CMap::RemoveKey
- AFXTEMPL/CMap::SetAt
helpviewer_keywords:
- CMap [MFC], CPair
- CMap [MFC], CMap
- CMap [MFC], GetCount
- CMap [MFC], GetHashTableSize
- CMap [MFC], GetNextAssoc
- CMap [MFC], GetSize
- CMap [MFC], GetStartPosition
- CMap [MFC], InitHashTable
- CMap [MFC], IsEmpty
- CMap [MFC], Lookup
- CMap [MFC], PGetFirstAssoc
- CMap [MFC], PGetNextAssoc
- CMap [MFC], PLookup
- CMap [MFC], RemoveAll
- CMap [MFC], RemoveKey
- CMap [MFC], SetAt
ms.assetid: 640a45ab-0993-4def-97ec-42cc78eb10b9
ms.openlocfilehash: fbb34d4db41ef11cd01a6a8a7f20cafa0e737268
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749072"
---
# <a name="cmap-class"></a>Klasa CMap

Klasa kolekcji słownika, która mapuje unikatowe klucze do wartości.

## <a name="syntax"></a>Składnia

```
template<class KEY, class ARG_KEY, class VALUE, class ARG_VALUE>class CMap : public CObject
```

#### <a name="parameters"></a>Parametry

*Klucz*<br/>
Klasa obiektu używanego jako klucz do mapy.

*ARG_KEY*<br/>
Typ danych używany dla argumentów *KEY;* zwykle odniesienie do *KEY*.

*Wartość*<br/>
Klasa obiektu przechowywanego na mapie.

*ARG_VALUE*<br/>
Typ danych używany dla argumentów *WARTOŚĆ;* zwykle odniesienie do *WARTOŚCI*.

## <a name="members"></a>Elementy członkowskie

### <a name="public-structures"></a>Struktury publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMap::CPair](#cpair)|Struktura zagnieżdżona zawierająca wartość klucza i wartość skojarzonego obiektu.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMap::CMap](#cmap)|Tworzy kolekcję, która mapuje klucze do wartości.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMap::GetCount](#getcount)|Zwraca liczbę elementów na tej mapie.|
|[CMap::GetHashTableSize](#gethashtablesize)|Zwraca liczbę elementów w tabeli mieszania.|
|[CMap::GetNextAssoc](#getnextassoc)|Pobiera następny element do iteracji.|
|[CMap::GetSize](#getsize)|Zwraca liczbę elementów na tej mapie.|
|[CMap::GetStartPosition](#getstartposition)|Zwraca położenie pierwszego elementu.|
|[CMap::InitHashTable](#inithashtable)|Inicjuje tabelę mieszania i określa jej rozmiar.|
|[CMap::IsEmpty](#isempty)|Testy stanu pustej mapy (bez elementów).|
|[CMap::Odnośnik](#lookup)|Wyszukuje wartość mapowane do danego klucza.|
|[CMap::PGetFirstAssoc](#pgetfirstassoc)|Zwraca wskaźnik do pierwszego elementu.|
|[CMap::PGetNextAssoc](#pgetnextassoc)|Pobiera wskaźnik do następnego elementu do iteracji.|
|[CMap::PLookup](#plookup)|Zwraca wskaźnik do klucza, którego wartość odpowiada określonej wartości.|
|[CMap::Usuńwszywszystko](#removeall)|Usuwa wszystkie elementy z tej mapy.|
|[CMap::RemoveKey](#removekey)|Usuwa element określony przez klucz.|
|[CMap::SetAt](#setat)|Wstawia element do mapy; zastępuje istniejący element, jeśli zostanie znaleziony pasujący klucz.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMap::operator \[\]](#operator_at)|Wstawia element do mapy — `SetAt`zastępowanie operatora dla .|

## <a name="remarks"></a>Uwagi

Po wstawieniu pary klucz-wartość (element) do mapy, można skutecznie pobrać lub usunąć parę za pomocą klucza, aby uzyskać do niej dostęp. Można również iterować na wszystkich elementów na mapie.

Zmienna typu POSITION jest używana do alternatywnego dostępu do wpisów. Możesz użyć pozycji, aby "zapamiętać" wpis i iterować przez mapę. Można by pomyśleć, że ta iteracja jest sekwencyjna według wartości klucza; tak nie jest. Sekwencja pobranych elementów jest nieokreślona.

Niektóre funkcje członkowskie tej klasy wywołać globalne funkcje pomocnika, `CMap` które muszą być dostosowane do większości zastosowań klasy. Zobacz [Pomocników klas kolekcji](../../mfc/reference/collection-class-helpers.md) w sekcji Makra i Globals **odwołania MFC**.

`CMap`zastępuje [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) do obsługi serializacji i dumpingu jego elementów. Jeśli mapa jest przechowywana `Serialize`w archiwum przy użyciu, każdy element mapy jest serializowany po kolei. Domyślna implementacja `SerializeElements` funkcji pomocnika wykonuje zapis bitowy. Aby uzyskać informacje na temat serializacji `CObject` elementów kolekcji wskaźnika pochodzących z lub innych typów zdefiniowanych przez użytkownika, zobacz [Jak: Zrobić kolekcję bezpieczną](../../mfc/how-to-make-a-type-safe-collection.md)dla typu .

Jeśli potrzebujesz zrzutu diagnostycznego poszczególnych elementów na mapie (klucze i wartości), należy ustawić głębokość kontekstu zrzutu na 1 lub większą.

Po `CMap` usunięciu obiektu lub usunięciu jego elementów klucze i wartości są usuwane.

Wyprowadzenie klasy mapy jest podobne do wyprowadzania listy. Zobacz artykuł [Kolekcje](../../mfc/collections.md) na ilustrację wyprowadzenia klasy listy specjalnego przeznaczenia.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CMap`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtempl.h

## <a name="cmapcmap"></a><a name="cmap"></a>CMap::CMap

Konstruuje pustą mapę.

```
CMap(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Parametry

*nBlockSize (Rozmiar)*<br/>
Określa szczegółowość alokacji pamięci w celu rozszerzenia mapy.

### <a name="remarks"></a>Uwagi

Wraz z rozwojem mapy pamięć jest przydzielana w jednostkach wpisów *nBlockSize.*

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#56](../../mfc/codesnippet/cpp/cmap-class_1.cpp)]

## <a name="cmapcpair"></a><a name="cpair"></a>CMap::CPair

Zawiera wartość klucza i wartość skojarzonego obiektu.

### <a name="remarks"></a>Uwagi

Jest to struktura zagnieżdżona w klasie [CMap](../../mfc/reference/cmap-class.md).

Struktura składa się z dwóch pól:

- `key`Rzeczywista wartość typu klucza.

- `value`Wartość skojarzonego obiektu.

Służy do przechowywania zwracanych wartości z [CMap::PLookup](#plookup), [CMap::PGetFirstAssoc](#pgetfirstassoc)i [CMap::PGetNextAssoc](#pgetnextassoc).

### <a name="example"></a>Przykład

Przykład użycia można znaleźć w przykładzie [CMap::PLookup](#plookup).

## <a name="cmapgetcount"></a><a name="getcount"></a>CMap::GetCount

Pobiera liczbę elementów na mapie.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów.

### <a name="example"></a>Przykład

Zobacz przykład [CMap::Lookup](#lookup).

## <a name="cmapgethashtablesize"></a><a name="gethashtablesize"></a>CMap::GetHashTableSize

Określa liczbę elementów w tabeli skrótów dla mapy.

```
UINT GetHashTableSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w tabeli mieszania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#57](../../mfc/codesnippet/cpp/cmap-class_2.cpp)]

## <a name="cmapgetnextassoc"></a><a name="getnextassoc"></a>CMap::GetNextAssoc

Pobiera element mapy `rNextPosition`w , `rNextPosition` a następnie aktualizacje, aby odwołać się do następnego elementu na mapie.

```cpp
void GetNextAssoc(
    POSITION& rNextPosition,
    KEY& rKey,
    VALUE& rValue) const;
```

### <a name="parameters"></a>Parametry

*rNastępna pozycja*<br/>
Określa odwołanie do wartości POSITION zwróconej `GetNextAssoc` `GetStartPosition` przez poprzedni lub wywołanie.

*Klucz*<br/>
Parametr szablonu określający typ klucza mapy.

*rKey (Klawisz)*<br/>
Określa zwracany klucz pobranego elementu.

*Wartość*<br/>
Parametr szablonu określający typ wartości mapy.

*rWartość*<br/>
Określa zwracaną wartość pobranego elementu.

### <a name="remarks"></a>Uwagi

Ta funkcja jest najbardziej przydatna do iteracji przez wszystkie elementy na mapie. Należy zauważyć, że sekwencja pozycji nie musi być taka sama jak sekwencja wartości klucza.

Jeśli pobrany element jest ostatnim na mapie, nowa wartość *rNextPosition* jest ustawiona na WARTOŚĆ NULL.

### <a name="example"></a>Przykład

Zobacz przykład [CMap::SetAt](#setat).

## <a name="cmapgetsize"></a><a name="getsize"></a>CMap::GetSize

Zwraca liczbę elementów mapy.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów na mapie.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby pobrać liczbę elementów na mapie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]

## <a name="cmapgetstartposition"></a><a name="getstartposition"></a>CMap::GetStartPosition

Rozpoczyna iterację mapy, zwracając wartość POSITION, która może `GetNextAssoc` zostać przekazana do wywołania.

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość POSITION wskazująca pozycję początkową dla iteracji mapy; lub NULL, jeśli mapa jest pusta.

### <a name="remarks"></a>Uwagi

Sekwencja iteracji nie jest przewidywalna; w związku z tym "pierwszy element na mapie" nie ma szczególnego znaczenia.

### <a name="example"></a>Przykład

Zobacz przykład [CMap::SetAt](#setat).

## <a name="cmapinithashtable"></a><a name="inithashtable"></a>CMap::InitHashTable

Inicjuje tabelę mieszania.

```cpp
void InitHashTable(UINT hashSize, BOOL  bAllocNow = TRUE);
```

### <a name="parameters"></a>Parametry

*rozmiar hashSize*<br/>
Liczba wpisów w tabeli mieszania.

*bLokalnyTeraz*<br/>
Jeśli true, przydziela tabelę mieszania podczas inicjowania; w przeciwnym razie tabela jest przydzielana w razie potrzeby.

### <a name="remarks"></a>Uwagi

Aby uzyskać najlepszą wydajność, rozmiar tabeli mieszania powinien być liczbą pierwszą. Aby zminimalizować kolizje, rozmiar powinien być o około 20 procent większy niż największy przewidywany zestaw danych.

### <a name="example"></a>Przykład

Zobacz przykład [CMap::Lookup](#lookup).

## <a name="cmapisempty"></a><a name="isempty"></a>CMap::IsEmpty

Określa, czy mapa jest pusta.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli ta mapa nie zawiera żadnych elementów; w przeciwnym razie 0.

### <a name="example"></a>Przykład

Zobacz przykład [CMap::RemoveAll](#removeall).

## <a name="cmaplookup"></a><a name="lookup"></a>CMap::Odnośnik

Wyszukuje wartość mapowane do danego klucza.

```
BOOL Lookup(ARG_KEY key, VALUE& rValue) const;
```

### <a name="parameters"></a>Parametry

*ARG_KEY*<br/>
Parametr szablonu określający typ wartości *klucza.*

*key*<br/>
Określa klucz identyfikujący element, który ma być wyszukany.

*Wartość*<br/>
Określa typ wartości, która ma być wyszukany.

*rWartość*<br/>
Odbiera wartość wyszukiwania.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli element został znaleziony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`Lookup`używa algorytmu mieszania, aby szybko znaleźć element mapy z kluczem, który dokładnie odpowiada danego klucza.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]

## <a name="cmapoperator--"></a><a name="operator_at"></a>CMap::operator [ ]

Wygodny substytut funkcji `SetAt` elementu członkowskiego.

```
VALUE& operator[](arg_key key);
```

### <a name="parameters"></a>Parametry

*Wartość*<br/>
Parametr szablonu określający typ wartości mapy.

*ARG_KEY*<br/>
Parametr szablonu określający typ wartości klucza.

*key*<br/>
Klucz używany do pobierania wartości z mapy.

### <a name="remarks"></a>Uwagi

W ten sposób może być używany tylko po lewej stronie instrukcji przypisania (wartość l). Jeśli nie ma żadnego elementu mapy z określonym kluczem, tworzony jest nowy element.

Nie ma "prawej strony" (r-value) równoważne tego operatora, ponieważ istnieje możliwość, że klucz nie można znaleźć na mapie. Użyj `Lookup` funkcji elementu członkowskiego do pobierania elementu.

### <a name="example"></a>Przykład

Zobacz przykład [CMap::Lookup](#lookup).

## <a name="cmappgetfirstassoc"></a><a name="pgetfirstassoc"></a>CMap::PGetFirstAssoc

Zwraca pierwszy wpis obiektu mapy.

```
const CPair* PGetFirstAssoc() const;
CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pierwszego wpisu na mapie; zobacz [CMap::CPair](#cpair). Jeśli mapa nie zawiera żadnych wpisów, wartość jest NULL.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby zwrócić wskaźnik pierwszy element w obiekcie mapy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#59](../../mfc/codesnippet/cpp/cmap-class_4.cpp)]

## <a name="cmappgetnextassoc"></a><a name="pgetnextassoc"></a>CMap::PGetNextAssoc

Pobiera element mapy wskazany przez *pAssocRec*.

```
const CPair *PGetNextAssoc(const CPair* pAssocRet) const;

CPair *PGetNextAssoc(const CPair* pAssocRet);
```

### <a name="parameters"></a>Parametry

*pAssocRet*<br/>
Wskazuje na wpis mapy zwrócony przez poprzednie [wywołanie PGetNextAssoc](#pgetnextassoc) lub [CMap::PGetFirstAssoc.](#pgetfirstassoc)

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do następnego wpisu na mapie; zobacz [CMap::CPair](#cpair). Jeśli element jest ostatni na mapie, wartość jest NULL.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby iterować za pośrednictwem wszystkich elementów na mapie. Pobierz pierwszy element z wywołaniem, `PGetFirstAssoc` a następnie iterować za `PGetNextAssoc`pośrednictwem mapy z kolejnymi wywołaniami .

### <a name="example"></a>Przykład

Zobacz przykład [CMap::PGetFirstAssoc](#pgetfirstassoc).

## <a name="cmapplookup"></a><a name="plookup"></a>CMap::PLookup

Znajduje wartość mapowane do danego klucza.

```
const CPair* PLookup(ARG_KEY key) const;
CPair* PLookup(ARG_KEY key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klucz dla elementu, który ma być wyszukiwany.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do struktury klucza; zobacz [CMap::CPair](#cpair). Jeśli nie zostanie `CMap::PLookup` znalezione żadne dopasowanie, zwraca wartość NULL.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby wyszukać element mapy z kluczem, który dokładnie pasuje do danego klucza.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#60](../../mfc/codesnippet/cpp/cmap-class_5.cpp)]

## <a name="cmapremoveall"></a><a name="removeall"></a>CMap::Usuńwszywszystko

Usuwa wszystkie wartości z tej mapy, wywołując `DestructElements`funkcję globalnego pomocnika .

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Uwagi

Funkcja działa poprawnie, jeśli mapa jest już pusta.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#61](../../mfc/codesnippet/cpp/cmap-class_6.cpp)]

## <a name="cmapremovekey"></a><a name="removekey"></a>CMap::RemoveKey

Wyszukuje wpis mapy odpowiadający dostarczonemu kluczowi; następnie, jeśli zostanie znaleziony klucz, usuwa wpis.

```
BOOL RemoveKey(ARG_KEY key);
```

### <a name="parameters"></a>Parametry

*ARG_KEY*<br/>
Parametr szablonu określający typ klucza.

*key*<br/>
Klucz do usunięcia elementu.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wpis został znaleziony i pomyślnie usunięte; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Funkcja `DestructElements` pomocnika służy do usuwania wpisu.

### <a name="example"></a>Przykład

Zobacz przykład [CMap::SetAt](#setat).

## <a name="cmapsetat"></a><a name="setat"></a>CMap::SetAt

Podstawowy oznacza wstawienie elementu do mapy.

```cpp
void SetAt(ARG_KEY key, ARG_VALUE newValue);
```

### <a name="parameters"></a>Parametry

*ARG_KEY*<br/>
Parametr szablonu określający typ parametru *klucza.*

*key*<br/>
Określa klucz nowego elementu.

*ARG_VALUE*<br/>
Parametr szablonu określający typ *parametru newValue.*

*Newvalue*<br/>
Określa wartość nowego elementu.

### <a name="remarks"></a>Uwagi

Po pierwsze, klucz jest spojrzał w górę. Jeśli zostanie znaleziony klucz, odpowiednia wartość zostanie zmieniona; w przeciwnym razie zostanie utworzona nowa para klucz-wartość.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#62](../../mfc/codesnippet/cpp/cmap-class_7.cpp)]

## <a name="see-also"></a>Zobacz też

[MFC Próbki COLLECT](../../overview/visual-cpp-samples.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
