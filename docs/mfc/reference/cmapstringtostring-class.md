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
ms.openlocfilehash: a2ffcf7ce7ee6eccc56382501a5969ddec6c9e22
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442590"
---
# <a name="cmapstringtostring-class"></a>Klasa CMapStringToString

Obsługuje mapy `CString` obiektów, które są objęte `CString` obiektami.

## <a name="syntax"></a>Składnia

```
class CMapStringToString : public CObject
```

## <a name="members"></a>Elementy członkowskie

Funkcje składowe `CMapStringToString` są podobne do funkcji składowych klasy [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md). W związku z tym podobieństwem można użyć dokumentacji referencyjnej `CMapStringToOb` dla specyficznych dla funkcji składowych. Wszędzie tam, gdzie widzisz wskaźnik `CObject` jako wartość zwracana lub parametr funkcji "output", Zastąp wskaźnik do **znaku**. Wszędzie tam, gdzie widzisz wskaźnik `CObject` jako parametr funkcji "Input", Zastąp wskaźnik do **znaku**.

`BOOL CMapStringToString::Lookup(LPCTSTR<key>, CString&<rValue>) const;`

na przykład tłumaczy na

`BOOL CMapStringToOb::Lookup(const char*<key>, CObject*&<rValue>) const;`

### <a name="public-structures"></a>Struktury publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CMapStringToString::CPair](#cpair)|Zagnieżdżona struktura zawierająca wartość klucza i wartość skojarzonego obiektu ciągu.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CMapStringToString::CMapStringToString](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
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
|[CMapStringToString::P GetFirstAssoc](#pgetfirstassoc)|Pobiera wskaźnik do pierwszego `CString` na mapie.|
|[CMapStringToString::P GetNextAssoc](#pgetnextassoc)|Pobiera wskaźnik do następnego `CString` do iteracji.|
|[CMapStringToString: wyszukiwanie:P](#plookup)|Zwraca wskaźnik do `CString`, którego wartość pasuje do określonej wartości.|
|[CMapStringToString::](../../mfc/reference/cmapstringtoob-class.md#removeall)|Usuwa wszystkie elementy z tej mapy.|
|[CMapStringToString::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Usuwa element określony przez klucz.|
|[CMapStringToString::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|Wstawia element do mapy; Zastępuje istniejący element, jeśli zostanie znaleziony pasujący klucz.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CMapStringToString:: operator \[ \]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Wstawia element do mapy — podstawienie operatora dla `SetAt`.|

## <a name="remarks"></a>Uwagi

`CMapStringToString` zawiera `IMPLEMENT_SERIAL` makro do obsługi serializacji i dumpingu jego elementów. Każdy element jest serializowany, jeśli mapa jest przechowywana w archiwum, za pomocą operatora przeciążonego wstawiania ( **<<** ) lub funkcji członkowskiej `Serialize`.

Jeśli potrzebujesz zrzutu poszczególnych `CString`- `CString` elementów, należy ustawić głębokość kontekstu zrzutu na 1 lub większą.

Po usunięciu obiektu `CMapStringToString` lub po usunięciu jego elementów obiekty `CString` są usuwane zgodnie z potrzebami.

Aby uzyskać więcej informacji na temat `CMapStringToString`, zobacz [kolekcje](../../mfc/collections.md)artykułów.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToString`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcoll. h

##  <a name="cpair"></a>CMapStringToString::CPair

Zawiera wartość klucza i wartość skojarzonego obiektu ciągu.

### <a name="remarks"></a>Uwagi

Jest to struktura zagnieżdżona w klasie [CMapStringToString](../../mfc/reference/cmapstringtostring-class.md).

Struktura składa się z dwóch pól:

- `key` wartość rzeczywistą typu klucza.

- `value` wartość skojarzonego obiektu.

Służy do przechowywania wartości zwracanych z [CMapStringToString::P Lookup](#plookup), [CMapStringToString::P getfirstassoc](#pgetfirstassoc)i [CMapStringToString::P GetNextAssoc](#pgetnextassoc).

### <a name="example"></a>Przykład

  Aby zapoznać się z przykładem użycia, zobacz przykład dla [CMapStringToString::P Lookup](#plookup).

##  <a name="pgetfirstassoc"></a>CMapStringToString::P GetFirstAssoc

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

##  <a name="pgetnextassoc"></a>CMapStringToString::P GetNextAssoc

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

Wywołaj tę metodę, aby wykonać iterację wszystkich elementów na mapie. Pobierz pierwszy element z wywołaniem do `PGetFirstAssoc`, a następnie wykonaj iterację mapy z kolejnymi wywołaniami `PGetNextAssoc`.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CMapStringToString::P getfirstassoc](#pgetfirstassoc).

##  <a name="plookup"></a>CMapStringToString: wyszukiwanie:P

Wyszukuje wartość zamapowane na dany klucz.

```
const CPair* PLookup(LPCTSTR key) const;

CPair* PLookup(LPCTSTR key);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Wskaźnik do klucza dla elementu, który ma być wyszukiwany.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do określonego klucza.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby wyszukać element mapy z kluczem, który dokładnie pasuje do podanego klucza.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#74](../../mfc/codesnippet/cpp/cmapstringtostring-class_2.cpp)]

## <a name="see-also"></a>Zobacz też

[ZBIERANIE próbek MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
