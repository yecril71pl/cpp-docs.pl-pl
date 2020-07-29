---
title: Klasa CMapStringToString
ms.date: 11/04/2016
f1_keywords:
- CMapStringToString
- AFXCOLL/CMapStringToString
- AFXCOLL/CMapStringToString::CPair
- AFXCOLL/CMapStringToString::CMapStringToString
- AFXCOLL/CMapStringToString::GetCount
- AFXCOLL/CMapStringToString::GetHashTableSize
- AFXCOLL/CMapStringToString::GetNextAssoc
- AFXCOLL/CMapStringToString::GetSize
- AFXCOLL/CMapStringToString::GetStartPosition
- AFXCOLL/CMapStringToString::HashKey
- AFXCOLL/CMapStringToString::InitHashTable
- AFXCOLL/CMapStringToString::IsEmpty
- AFXCOLL/CMapStringToString::Lookup
- AFXCOLL/CMapStringToString::LookupKey
- AFXCOLL/CMapStringToString::PGetFirstAssoc
- AFXCOLL/CMapStringToString::PGetNextAssoc
- AFXCOLL/CMapStringToString::PLookup
- AFXCOLL/CMapStringToString::RemoveAll
- AFXCOLL/CMapStringToString::RemoveKey
- AFXCOLL/CMapStringToString::SetAt
helpviewer_keywords:
- CMapStringToString [MFC], CPair
- CMapStringToString [MFC], CMapStringToString
- CMapStringToString [MFC], GetCount
- CMapStringToString [MFC], GetHashTableSize
- CMapStringToString [MFC], GetNextAssoc
- CMapStringToString [MFC], GetSize
- CMapStringToString [MFC], GetStartPosition
- CMapStringToString [MFC], HashKey
- CMapStringToString [MFC], InitHashTable
- CMapStringToString [MFC], IsEmpty
- CMapStringToString [MFC], Lookup
- CMapStringToString [MFC], LookupKey
- CMapStringToString [MFC], PGetFirstAssoc
- CMapStringToString [MFC], PGetNextAssoc
- CMapStringToString [MFC], PLookup
- CMapStringToString [MFC], RemoveAll
- CMapStringToString [MFC], RemoveKey
- CMapStringToString [MFC], SetAt
ms.assetid: b45794c2-fe6b-4edb-a8ca-faa03b57b4a8
ms.openlocfilehash: 28422c26ba2ca77657bfcf166592d2bc69169891
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223008"
---
# <a name="cmapstringtostring-class"></a>Klasa CMapStringToString

Obsługuje mapy `CString` obiektów objętych przez `CString` obiekty.

## <a name="syntax"></a>Składnia

```
class CMapStringToString : public CObject
```

## <a name="members"></a>Elementy członkowskie

Funkcje składowe `CMapStringToString` są podobne do funkcji składowych klasy [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md). W związku z tym podobieństwem można użyć `CMapStringToOb` dokumentacji referencyjnej dla specyficznych dla funkcji składowych. Wszędzie tam, gdzie widzisz `CObject` wskaźnik jako wartość zwrotną lub parametr funkcji "output", Zastąp wskaźnik do **`char`** . Wszędzie tam, gdzie widzisz `CObject` wskaźnik jako parametr funkcji "Input", Zastąp wskaźnik do **`char`** .

`BOOL CMapStringToString::Lookup(LPCTSTR<key>, CString&<rValue>) const;`

na przykład tłumaczy na

`BOOL CMapStringToOb::Lookup(const char*<key>, CObject*&<rValue>) const;`

### <a name="public-structures"></a>Struktury publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMapStringToString::CPair](#cpair)|Zagnieżdżona struktura zawierająca wartość klucza i wartość skojarzonego obiektu ciągu.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMapStringToString::CMapStringToString](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMapStringToString:: GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Zwraca liczbę elementów w tej mapie.|
|[CMapStringToString::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Określa bieżącą liczbę elementów w tabeli skrótów.|
|[CMapStringToString::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Pobiera następny element do iteracji.|
|[CMapStringToString:: GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|Zwraca liczbę elementów w tej mapie.|
|[CMapStringToString::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Zwraca pozycję pierwszego elementu.|
|[CMapStringToString::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Oblicza wartość skrótu określonego klucza.|
|[CMapStringToString::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Inicjuje tablicę skrótów.|
|[CMapStringToString:: IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Testuje warunek pustej mapy (nie elementy).|
|[CMapStringToString:: Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Wyszukuje wskaźnik void na podstawie klucza wskaźnika void. Wartość wskaźnika, a nie jednostka, do której wskazuje, jest używana do porównania klucza.|
|[CMapStringToString:: LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Zwraca odwołanie do klucza skojarzonego z określoną wartością klucza.|
|[CMapStringToString::P GetFirstAssoc](#pgetfirstassoc)|Pobiera wskaźnik do pierwszego elementu `CString` w mapie.|
|[CMapStringToString::P GetNextAssoc](#pgetnextassoc)|Pobiera wskaźnik do następnego `CString` do iteracji.|
|[CMapStringToString: wyszukiwanie:P](#plookup)|Zwraca wskaźnik do `CString` którego wartość jest zgodna z określoną wartością.|
|[CMapStringToString::](../../mfc/reference/cmapstringtoob-class.md#removeall)|Usuwa wszystkie elementy z tej mapy.|
|[CMapStringToString::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Usuwa element określony przez klucz.|
|[CMapStringToString::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|Wstawia element do mapy; Zastępuje istniejący element, jeśli zostanie znaleziony pasujący klucz.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMapStringToString:: operator \[\]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Wstawia element do mapy — podstawienia operatora dla `SetAt` .|

## <a name="remarks"></a>Uwagi

`CMapStringToString`zawiera `IMPLEMENT_SERIAL` makro obsługujące serializację i zatopienie swoich elementów. Każdy element jest serializowany, jeśli mapa jest przechowywana w archiwum, przy użyciu przeciążonego operatora wstawiania ( **<<** ) lub `Serialize` funkcji członkowskiej.

Jeśli potrzebujesz zrzutu poszczególnych `CString` -  `CString` elementów, musisz ustawić głębokość kontekstu zrzutu na 1 lub większą.

Po `CMapStringToString` usunięciu obiektu lub po usunięciu jego elementów `CString` obiekty są usuwane zgodnie z potrzebami.

Aby uzyskać więcej informacji na temat `CMapStringToString` , zobacz [kolekcje](../../mfc/collections.md)artykułów.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToString`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcoll. h

## <a name="cmapstringtostringcpair"></a><a name="cpair"></a>CMapStringToString::CPair

Zawiera wartość klucza i wartość skojarzonego obiektu ciągu.

### <a name="remarks"></a>Uwagi

Jest to struktura zagnieżdżona w klasie [CMapStringToString](../../mfc/reference/cmapstringtostring-class.md).

Struktura składa się z dwóch pól:

- `key`Rzeczywista wartość typu klucza.

- `value`Wartość skojarzonego obiektu.

Służy do przechowywania wartości zwracanych z [CMapStringToString::P Lookup](#plookup), [CMapStringToString::P getfirstassoc](#pgetfirstassoc)i [CMapStringToString::P GetNextAssoc](#pgetnextassoc).

### <a name="example"></a>Przykład

  Aby zapoznać się z przykładem użycia, zobacz przykład dla [CMapStringToString::P Lookup](#plookup).

## <a name="cmapstringtostringpgetfirstassoc"></a><a name="pgetfirstassoc"></a>CMapStringToString::P GetFirstAssoc

Zwraca pierwszy wpis obiektu mapy.

```
const CPair* PGetFirstAssoc() const;

CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pierwszego wpisu na mapie; Zobacz [CMapStringToString:: CPair](#cpair). Jeśli mapa jest pusta, wartość jest RÓWNa NULL.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby zwrócić wskaźnik do pierwszego elementu w obiekcie mapy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#73](../../mfc/codesnippet/cpp/cmapstringtostring-class_1.cpp)]

## <a name="cmapstringtostringpgetnextassoc"></a><a name="pgetnextassoc"></a>CMapStringToString::P GetNextAssoc

Pobiera element mapy wskazywany przez *pAssocRec*.

```
const CPair *PGetNextAssoc(const CPair* pAssoc) const;

CPair *PGetNextAssoc(const CPair* pAssoc);
```

### <a name="parameters"></a>Parametry

*pAssoc*<br/>
Wskazuje na wpis mapy zwrócony przez poprzednie wywołanie [PGetNextAssoc](#pgetnextassoc) lub [PGetFirstAssoc](#pgetfirstassoc) .

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do następnego wpisu na mapie; Zobacz [CMapStringToString:: CPair](#cpair). Jeśli element jest ostatnim na mapie, wartość jest RÓWNa NULL.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby wykonać iterację wszystkich elementów na mapie. Pobranie pierwszego elementu z wywołaniem `PGetFirstAssoc` , a następnie iteracja przez mapę z kolejnymi wywołaniami do `PGetNextAssoc` .

### <a name="example"></a>Przykład

  Zobacz przykład dla [CMapStringToString::P getfirstassoc](#pgetfirstassoc).

## <a name="cmapstringtostringplookup"></a><a name="plookup"></a>CMapStringToString: wyszukiwanie:P

Wyszukuje wartość zamapowane na dany klucz.

```
const CPair* PLookup(LPCTSTR key) const;

CPair* PLookup(LPCTSTR key);
```

### <a name="parameters"></a>Parametry

*głównych*<br/>
Wskaźnik do klucza dla elementu, który ma być wyszukiwany.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do określonego klucza.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby wyszukać element mapy z kluczem, który dokładnie pasuje do podanego klucza.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#74](../../mfc/codesnippet/cpp/cmapstringtostring-class_2.cpp)]

## <a name="see-also"></a>Zobacz także

[ZBIERANIE próbek MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
