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
ms.openlocfilehash: 58f9efb19988be8487ec87ce0c63d90ee1a97911
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62296582"
---
# <a name="cmap-class"></a>Klasa CMap

Klasa kolekcji słownika, która mapuje unikatowe klucze do wartości.

## <a name="syntax"></a>Składnia

```
template<class KEY, class ARG_KEY, class VALUE, class ARG_VALUE>class CMap : public CObject
```

#### <a name="parameters"></a>Parametry

*KEY*<br/>
Klasa Obiekt używany jako klucz do mapy.

*ARG_KEY*<br/>
Typ danych używany dla *klucz* argumentów; zazwyczaj odwołanie do *klucz*.

*WARTOŚĆ*<br/>
Klasa obiektu przechowywany w mapie.

*ARG_VALUE*<br/>
Typ danych używany dla *wartość* argumentów; zazwyczaj odwołanie do *wartość*.

## <a name="members"></a>Elementy członkowskie

### <a name="public-structures"></a>Publiczne struktury

|Nazwa|Opis|
|----------|-----------------|
|[CMap::CPair](#cpair)|Struktura zagnieżdżona zawierające wartości klucza i wartości skojarzonego obiektu.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMap::CMap](#cmap)|Konstruuje kolekcję mapujący klucze do wartości.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMap::GetCount](#getcount)|Zwraca liczbę elementów na tej mapie.|
|[CMap::GetHashTableSize](#gethashtablesize)|Zwraca liczbę elementów w tabeli wyznaczania wartości skrótu.|
|[CMap::GetNextAssoc](#getnextassoc)|Pobiera następny element do wykonania iteracji.|
|[CMap::GetSize](#getsize)|Zwraca liczbę elementów na tej mapie.|
|[CMap::GetStartPosition](#getstartposition)|Zwraca pozycję pierwszego elementu.|
|[CMap::InitHashTable](#inithashtable)|Inicjuje tabelę mieszania oraz określa jego rozmiar.|
|[CMap::IsEmpty](#isempty)|Testuje pod kątem warunku pusta Mapa (Brak elementów).|
|[CMap::Lookup](#lookup)|Wyszukuje wartość mapowane do danego klucza.|
|[CMap::PGetFirstAssoc](#pgetfirstassoc)|Zwraca wskaźnik do pierwszego elementu.|
|[CMap::PGetNextAssoc](#pgetnextassoc)|Pobiera wskaźnik do następnego elementu do wykonania iteracji.|
|[CMap::PLookup](#plookup)|Zwraca wskaźnik do klucza, którego wartość odpowiada określonej wartości.|
|[CMap::RemoveAll](#removeall)|Usuwa wszystkie elementy z tej mapie.|
|[CMap::RemoveKey](#removekey)|Usuwa element określony przez klucz.|
|[CMap::SetAt](#setat)|Wstawia element do mapy; zastępuje istniejący element, jeśli dopasowany klucz zostanie znaleziony.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMap::operator \[ \]](#operator_at)|Wstawia element do mapy — operator podstawienia dla `SetAt`.|

## <a name="remarks"></a>Uwagi

Po wstawieniu pary klucz wartość (element) do mapy efektywnie można pobrać lub usunąć pary przy użyciu klucza dostępu do niego. Można również wykonać iterację przez wszystkie elementy na mapie.

Zmienna typu pozycja jest używany dla alternatywny dostęp do wpisów. Można użyć pozycji, wpis "pamiętać" i do iteracji na mapie. Może się wydawać, sekwencyjnych według wartości kluczy; to tej iteracji nie jest dostępne. Sekwencja elementów pobrane jest nieokreślony.

Niektóre funkcje Członkowskie to wywołanie klasy, funkcje globalne pomocy, które muszą być dostosowane dla większości zastosowań `CMap` klasy. Zobacz [pomocnicy klasy kolekcji](../../mfc/reference/collection-class-helpers.md) w sekcji makra i funkcje globalne **odwołanie MFC**.

`CMap` zastępuje [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) do obsługi serializacji i zrzucanie z jego elementów. Jeśli mapa jest przechowywany za pomocą archiwum `Serialize`, każdy element mapy jest serializowana z osobna. Domyślna implementacja klasy `SerializeElements` funkcja pomocnicza jest bitowe zapisu. Dla informacji o serializacji elementów kolekcji wskaźnika pochodną `CObject` lub innych typów zdefiniowanych przez użytkownika, zobacz [jak: Tworzenie bezpiecznej kolekcji](../../mfc/how-to-make-a-type-safe-collection.md).

Diagnostyczne zrzut poszczególnych elementów w mapie (klucze i wartości), należy należy ustawić głębokość kontekstu zrzutu do 1 lub większą.

Gdy `CMap` obiekt zostanie usunięty lub po jego elementy są usuwane, klucze i wartości są usuwane.

Wyprowadzanie klasy mapy jest podobny do wyprowadzania listy. Zapoznaj się z artykułem [kolekcje](../../mfc/collections.md) ilustrację pochodnym klasy listy specjalnych.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CMap`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtempl.h

##  <a name="cmap"></a>  CMap::CMap

Tworzy pusty mapy.

```
CMap(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Parametry

*nBlockSize*<br/>
Określa stopień szczegółowości alokacji pamięci do rozszerzania możliwości programu na mapie.

### <a name="remarks"></a>Uwagi

Wraz z rozwojem mapy pamięć została przydzielona w jednostkach *nBlockSize* wpisów.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#56](../../mfc/codesnippet/cpp/cmap-class_1.cpp)]

##  <a name="cpair"></a>  CMap::CPair

Zawiera wartość klucza i wartości skojarzonego obiektu.

### <a name="remarks"></a>Uwagi

Jest to struktura zagnieżdżona w klasie [CMap](../../mfc/reference/cmap-class.md).

Struktura składa się z dwóch pól:

- `key` Wartość rzeczywista typ klucza.

- `value` Wartość skojarzonego obiektu.

Jest on używany do przechowywania wartości zwracanych z [CMap::PLookup](#plookup), [CMap::PGetFirstAssoc](#pgetfirstassoc), i [CMap::PGetNextAssoc](#pgetnextassoc).

### <a name="example"></a>Przykład

Na przykład użycia, zobacz przykład [CMap::PLookup](#plookup).

##  <a name="getcount"></a>  CMap::GetCount

Pobiera liczbę elementów w mapie.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów.

### <a name="example"></a>Przykład

Zobacz przykład [CMap::Lookup](#lookup).

##  <a name="gethashtablesize"></a>  CMap::GetHashTableSize

Określa liczbę elementów w tablicy skrótów do mapy.

```
UINT GetHashTableSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w tabeli wyznaczania wartości skrótu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#57](../../mfc/codesnippet/cpp/cmap-class_2.cpp)]

##  <a name="getnextassoc"></a>  CMap::GetNextAssoc

Pobiera element mapy w `rNextPosition`, następnie aktualizuje `rNextPosition` do odwoływania się do następnego elementu w mapie.

```
void GetNextAssoc(
    POSITION& rNextPosition,
    KEY& rKey,
    VALUE& rValue) const;
```

### <a name="parameters"></a>Parametry

*rNextPosition*<br/>
Określa odwołanie do wartości pozycji zwrócony przez poprzednie `GetNextAssoc` lub `GetStartPosition` wywołania.

*KEY*<br/>
Parametr szablonu określający typ klucza mapy.

*rKey*<br/>
Określa klucz zwróconego elementu pobrane.

*WARTOŚĆ*<br/>
Parametr szablonu określający typ wartości mapy.

*r-wartości*<br/>
Określa wartość elementu pobrane.

### <a name="remarks"></a>Uwagi

Ta funkcja jest najbardziej przydatne do iteracji na elementach na mapie. Należy pamiętać, że sekwencja pozycji niekoniecznie jest taka sama jak wartość klucza sekwencji.

Jeśli element pobrane jest ostatni w mapie, nowa wartość *rNextPosition* ma wartość NULL.

### <a name="example"></a>Przykład

Zobacz przykład [CMap::SetAt](#setat).

##  <a name="getsize"></a>  CMap::GetSize

Zwraca liczbę elementów mapy.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w mapie.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby pobrać liczbę elementów w mapie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]

##  <a name="getstartposition"></a>  CMap::GetStartPosition

Uruchamia iteracji mapy, zwracając wartość pozycji, które mogą być przekazywane do `GetNextAssoc` wywołania.

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość pozycji, która wskazuje pozycja początkowa które mapy; lub wartość NULL, jeśli mapa jest pusta.

### <a name="remarks"></a>Uwagi

Sekwencja iteracji nie jest przewidywalne; Dlatego "pierwszego elementu w mapie" ma specjalnego znaczenia.

### <a name="example"></a>Przykład

Zobacz przykład [CMap::SetAt](#setat).

##  <a name="inithashtable"></a>  CMap::InitHashTable

Inicjuje tabelę mieszania.

```
void InitHashTable(UINT hashSize, BOOL  bAllocNow = TRUE);
```

### <a name="parameters"></a>Parametry

*hashSize*<br/>
Liczba wpisów w tabeli wyznaczania wartości skrótu.

*bAllocNow*<br/>
W przypadku opcji TRUE przydziela tablicy skrótów po zainicjowaniu; w przeciwnym razie tabeli jest przydzielany, gdy potrzebne.

### <a name="remarks"></a>Uwagi

Aby uzyskać najlepszą wydajność rozmiar tabeli wyznaczania wartości skrótu powinien być liczba pierwsza. Aby zminimalizować konflikty, rozmiar powinien być około 20% większa niż największa przewidywanego zestawu danych.

### <a name="example"></a>Przykład

Zobacz przykład [CMap::Lookup](#lookup).

##  <a name="isempty"></a>  CMap::IsEmpty

Określa, czy mapa jest pusta.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to mapowanie nie zawiera elementów; w przeciwnym razie 0.

### <a name="example"></a>Przykład

Zobacz przykład [CMap::RemoveAll](#removeall).

##  <a name="lookup"></a>  CMap::Lookup

Wyszukuje wartość mapowane do danego klucza.

```
BOOL Lookup(ARG_KEY key, VALUE& rValue) const;
```

### <a name="parameters"></a>Parametry

*ARG_KEY*<br/>
Parametr szablonu określający typ *klucz* wartość.

*Klucz*<br/>
Określa klucz, który identyfikuje elementu, który ma być wyszukiwana.

*WARTOŚĆ*<br/>
Określa typ wartości ma być wyszukiwana.

*r-wartości*<br/>
Odbiera wartość oglądałem się w górę.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli element został znaleziony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`Lookup` używa algorytmu wyznaczania wartości skrótu, aby szybko znaleźć element mapy za pomocą klucza, który dokładnie pasuje do danego klucza.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]

##  <a name="operator_at"></a>  [] CMap::operator

Zastępuje wygodne `SetAt` funkcja elementu członkowskiego.

```
VALUE& operator[](arg_key key);
```

### <a name="parameters"></a>Parametry

*WARTOŚĆ*<br/>
Parametr szablonu określający typ wartości mapy.

*ARG_KEY*<br/>
Parametr szablonu określający typ wartości klucza.

*Klucz*<br/>
Klucz używany do pobierania wartości z mapy.

### <a name="remarks"></a>Uwagi

Dlatego może służyć tylko z lewej instrukcji przypisania (l wartości). Jeśli nie ma żadnego elementu na mapie, z określonym kluczem, nowy element zostanie utworzony.

Istnieje nie "po prawej stronie" (r) odpowiednikiem tego operatora, ponieważ istnieje możliwość, że nie można znaleźć klucza w mapie. Użyj `Lookup` funkcja elementu członkowskiego do elementu pobierania.

### <a name="example"></a>Przykład

Zobacz przykład [CMap::Lookup](#lookup).

##  <a name="pgetfirstassoc"></a>  CMap::PGetFirstAssoc

Zwraca pierwszy wpis obiektu mapy.

```
const CPair* PGetFirstAssoc() const;
CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pierwszej pozycji w mapowaniu; zobacz [CMap::CPair](#cpair). Jeśli mapa zawiera żadnych wpisów, wartość jest równa NULL.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby zwrócić wskaźnik do pierwszego elementu w obiektu mapy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#59](../../mfc/codesnippet/cpp/cmap-class_4.cpp)]

##  <a name="pgetnextassoc"></a>  CMap::PGetNextAssoc

Pobiera element mapy, wskazane przez *pAssocRec*.

```
const CPair *PGetNextAssoc(const CPair* pAssocRet) const;

CPair *PGetNextAssoc(const CPair* pAssocRet);
```

### <a name="parameters"></a>Parametry

*pAssocRet*<br/>
Wskazuje na wpis mapy zwrócony przez poprzednie [PGetNextAssoc](#pgetnextassoc) lub [CMap::PGetFirstAssoc](#pgetfirstassoc) wywołania.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do następnego wpisu w mapowaniu; zobacz [CMap::CPair](#cpair). Jeśli element jest ostatni w mapie, wartość jest wartością NULL.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę do iteracji wszystkich elementów w mapie. Pobrać pierwszy element z wywołaniem `PGetFirstAssoc` i następnie iterację mapy za pomocą kolejne wywołania `PGetNextAssoc`.

### <a name="example"></a>Przykład

Zobacz przykład [CMap::PGetFirstAssoc](#pgetfirstassoc).

##  <a name="plookup"></a>  CMap::PLookup

Wyszukuje wartość mapowane do danego klucza.

```
const CPair* PLookup(ARG_KEY key) const;
CPair* PLookup(ARG_KEY key);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Klucz elementu, który ma zostać wyszukany.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do struktury klucza; zobacz [CMap::CPair](#cpair). Jeśli nie zostanie znalezione dopasowanie, `CMap::PLookup` zwraca wartość NULL.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby wyszukać element mapy za pomocą klucza, który dokładnie pasuje do danego klucza.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#60](../../mfc/codesnippet/cpp/cmap-class_5.cpp)]

##  <a name="removeall"></a>  CMap::RemoveAll

Usuwa wszystkie wartości z tej mapy, przez wywołanie funkcji pomocnika globalnego `DestructElements`.

```
void RemoveAll();
```

### <a name="remarks"></a>Uwagi

Funkcja działa prawidłowo, jeśli mapa jest pusty.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#61](../../mfc/codesnippet/cpp/cmap-class_6.cpp)]

##  <a name="removekey"></a>  CMap::RemoveKey

Wyszukuje wpisu mapowania odpowiadający podany klucz; następnie Jeśli klucz zostanie znaleziony, usuwa wpis.

```
BOOL RemoveKey(ARG_KEY key);
```

### <a name="parameters"></a>Parametry

*ARG_KEY*<br/>
Parametr szablonu określający typ klucza.

*Klucz*<br/>
Klucz elementu do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli wpis zostało znalezione i pomyślnie usunął; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`DestructElements` Funkcji pomocnika służy do usuwania wpisu.

### <a name="example"></a>Przykład

Zobacz przykład [CMap::SetAt](#setat).

##  <a name="setat"></a>  CMap::SetAt

Podstawowy oznacza, że można wstawić elementu na mapie.

```
void SetAt(ARG_KEY key, ARG_VALUE newValue);
```

### <a name="parameters"></a>Parametry

*ARG_KEY*<br/>
Parametr szablonu określający typ *klucz* parametru.

*Klucz*<br/>
Określa klucz nowego elementu.

*ARG_VALUE*<br/>
Parametr szablonu określający typ *newValue* parametru.

*newValue*<br/>
Określa wartość nowego elementu.

### <a name="remarks"></a>Uwagi

Najpierw jest wyszukiwana klucza. Jeśli klucz zostanie znaleziony, a następnie odpowiednią wartość zostanie zmieniona; w przeciwnym razie jest tworzony nowy pary klucz wartość.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#62](../../mfc/codesnippet/cpp/cmap-class_7.cpp)]

## <a name="see-also"></a>Zobacz także

[Próbki MFC ZBIERANIE](../../overview/visual-cpp-samples.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
