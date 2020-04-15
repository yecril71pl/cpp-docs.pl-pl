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
ms.openlocfilehash: 544154569c50369b805ba296aa975849f245d4ad
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370115"
---
# <a name="cmapstringtostring-class"></a>Klasa CMapStringToString

Obsługuje mapy `CString` obiektów wpisywały się w `CString` obiekty.

## <a name="syntax"></a>Składnia

```
class CMapStringToString : public CObject
```

## <a name="members"></a>Elementy członkowskie

Funkcje członkowskie `CMapStringToString` są podobne do funkcji członkowskich klasy [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md). Ze względu na to podobieństwo `CMapStringToOb` można użyć dokumentacji referencyjnej dla specyfiki funkcji elementu członkowskiego. Wszędzie tam, `CObject` gdzie wskaźnik jest widoczny jako wartość zwracana lub parametr funkcji "output", zastąp wskaźnik **na char**. Wszędzie tam, `CObject` gdzie wskaźnik jest widoczny jako parametr funkcji "input", zastąp wskaźnik **na char**.

`BOOL CMapStringToString::Lookup(LPCTSTR<key>, CString&<rValue>) const;`

na przykład przekłada się na

`BOOL CMapStringToOb::Lookup(const char*<key>, CObject*&<rValue>) const;`

### <a name="public-structures"></a>Struktury publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMapStringToString::CPair](#cpair)|Struktura zagnieżdżona zawierająca wartość klucza i wartość skojarzonego obiektu ciągu.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMapStringToString::CMapStringToString](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMapStringToString::GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Zwraca liczbę elementów na tej mapie.|
|[CMapStringToString::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Określa bieżącą liczbę elementów w tabeli mieszania.|
|[CMapStringToString::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Pobiera następny element do iteracji.|
|[CMapStringToString::GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|Zwraca liczbę elementów na tej mapie.|
|[CMapStringToString::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Zwraca położenie pierwszego elementu.|
|[CMapStringToString::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Oblicza wartość mieszania określonego klucza.|
|[CMapStringToString::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Inicjuje tabelę mieszania.|
|[CMapStringToString::IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Testy stanu pustej mapy (bez elementów).|
|[CMapStringToString::Odnośnik](../../mfc/reference/cmapstringtoob-class.md#lookup)|Wyszukuje wskaźnik void na podstawie klucza wskaźnika void. Wartość wskaźnika, a nie encja, na której wskazuje, jest używana do porównywania kluczy.|
|[CMapStringToString::Klucz wyszukiwania](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Zwraca odwołanie do klucza skojarzonego z określoną wartością klucza.|
|[CMapStringToString::PGetFirstAssoc](#pgetfirstassoc)|Pobiera wskaźnik do `CString` pierwszego na mapie.|
|[CMapStringToString::PGetNextAssoc](#pgetnextassoc)|Pobiera wskaźnik do `CString` następnego do iteracji.|
|[CMapStringToString::PLookup](#plookup)|Zwraca wskaźnik do `CString` wartości, której wartość odpowiada określonej wartości.|
|[CMapStringToString::Usuńwszywszystki](../../mfc/reference/cmapstringtoob-class.md#removeall)|Usuwa wszystkie elementy z tej mapy.|
|[CMapStringToString::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Usuwa element określony przez klucz.|
|[CMapStringToString::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|Wstawia element do mapy; zastępuje istniejący element, jeśli zostanie znaleziony pasujący klucz.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMapStringToString::operator \[\]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Wstawia element do mapy — `SetAt`zastępowanie operatora dla .|

## <a name="remarks"></a>Uwagi

`CMapStringToString`zawiera makro `IMPLEMENT_SERIAL` w celu wspierania serializacji i dumpingu jego elementów. Każdy element jest serializowany po kolei, jeśli mapa jest przechowywana w **<<** archiwum, za `Serialize` pomocą przeciążonego operatora wstawiania ( ) lub z funkcją elementu członkowskiego.

Jeśli potrzebujesz zrzutu `CString` -  `CString` poszczególnych elementów, należy ustawić głębokość kontekstu zrzutu na 1 lub większą.

Po `CMapStringToString` usunięciu obiektu lub usunięciu jego elementów `CString` obiekty są usuwane odpowiednio.

Aby uzyskać `CMapStringToString`więcej informacji na temat , zobacz artykuł [Kolekcje](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CMapStringToString`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcoll.h

## <a name="cmapstringtostringcpair"></a><a name="cpair"></a>CMapStringToString::CPair

Zawiera wartość klucza i wartość skojarzonego obiektu ciągu.

### <a name="remarks"></a>Uwagi

Jest to struktura zagnieżdżona w klasie [CMapStringToString](../../mfc/reference/cmapstringtostring-class.md).

Struktura składa się z dwóch pól:

- `key`Rzeczywista wartość typu klucza.

- `value`Wartość skojarzonego obiektu.

Służy do przechowywania wartości zwracanych z [CMapStringToString::PLookup](#plookup), [CMapStringToString::PGetFirstAssoc](#pgetfirstassoc)i [CMapStringToString::PGetNextAssoc](#pgetnextassoc).

### <a name="example"></a>Przykład

  Na przykład użycia zobacz przykład [CMapStringToString::PLookup](#plookup).

## <a name="cmapstringtostringpgetfirstassoc"></a><a name="pgetfirstassoc"></a>CMapStringToString::PGetFirstAssoc

Zwraca pierwszy wpis obiektu mapy.

```
const CPair* PGetFirstAssoc() const;

CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pierwszego wpisu na mapie; zobacz [CMapStringToString::CPair](#cpair). Jeśli mapa jest pusta, wartość jest NULL.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby zwrócić wskaźnik pierwszy element w obiekcie mapy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#73](../../mfc/codesnippet/cpp/cmapstringtostring-class_1.cpp)]

## <a name="cmapstringtostringpgetnextassoc"></a><a name="pgetnextassoc"></a>CMapStringToString::PGetNextAssoc

Pobiera element mapy wskazany przez *pAssocRec*.

```
const CPair *PGetNextAssoc(const CPair* pAssoc) const;

CPair *PGetNextAssoc(const CPair* pAssoc);
```

### <a name="parameters"></a>Parametry

*pAssoc*<br/>
Wskazuje wpis mapy zwrócony przez poprzednie wywołanie [PGetNextAssoc](#pgetnextassoc) lub [PGetFirstAssoc.](#pgetfirstassoc)

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do następnego wpisu na mapie; zobacz [CMapStringToString::CPair](#cpair). Jeśli element jest ostatni na mapie, wartość jest NULL.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby iterować za pośrednictwem wszystkich elementów na mapie. Pobierz pierwszy element z wywołaniem, `PGetFirstAssoc` a następnie iterować za `PGetNextAssoc`pośrednictwem mapy z kolejnymi wywołaniami .

### <a name="example"></a>Przykład

  Zobacz przykład [CMapStringToString::PGetFirstAssoc](#pgetfirstassoc).

## <a name="cmapstringtostringplookup"></a><a name="plookup"></a>CMapStringToString::PLookup

Wyszukuje wartość mapowane do danego klucza.

```
const CPair* PLookup(LPCTSTR key) const;

CPair* PLookup(LPCTSTR key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Wskaźnik do klucza dla elementu, który ma być wyszukiwany.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do określonego klucza.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby wyszukać element mapy z kluczem, który dokładnie pasuje do danego klucza.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#74](../../mfc/codesnippet/cpp/cmapstringtostring-class_2.cpp)]

## <a name="see-also"></a>Zobacz też

[MFC Próbki COLLECT](../../overview/visual-cpp-samples.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
