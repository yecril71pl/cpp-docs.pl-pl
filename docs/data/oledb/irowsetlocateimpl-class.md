---
title: IRowsetLocateImpl — Klasa
ms.date: 11/04/2016
f1_keywords:
- IRowsetLocateImpl
- ATL.IRowsetLocateImpl.Compare
- IRowsetLocateImpl::Compare
- IRowsetLocateImpl.Compare
- ATL::IRowsetLocateImpl::Compare
- GetRowsAt
- IRowsetLocateImpl.GetRowsAt
- ATL::IRowsetLocateImpl::GetRowsAt
- IRowsetLocateImpl::GetRowsAt
- ATL.IRowsetLocateImpl.GetRowsAt
- IRowsetLocateImpl::GetRowsByBookmark
- IRowsetLocateImpl.GetRowsByBookmark
- GetRowsByBookmark
- IRowsetLocateImpl::Hash
- IRowsetLocateImpl.Hash
- m_rgBookmarks
- IRowsetLocateImpl::m_rgBookmarks
- ATL.IRowsetLocateImpl.m_rgBookmarks
- ATL::IRowsetLocateImpl::m_rgBookmarks
- IRowsetLocateImpl.m_rgBookmarks
helpviewer_keywords:
- providers, bookmarks
- IRowsetLocateImpl class
- bookmarks, OLE DB
- Compare method
- GetRowsAt method
- GetRowsByBookmark method
- Hash method
- m_rgbookmarks
ms.assetid: a8aa3149-7ce8-4976-a680-2da193fd3234
ms.openlocfilehash: 06e860425215d9fde268b780c001301b14a1caa1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210434"
---
# <a name="irowsetlocateimpl-class"></a>IRowsetLocateImpl — Klasa

Implementuje interfejs OLE DB [IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85)) , który pobiera dowolne wiersze z zestawu wierszy.

## <a name="syntax"></a>Składnia

```cpp
template <
   class T,
   class RowsetInterface,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap < RowClass::KeyType, RowClass* >,
   class BookmarkKeyType = LONG,
   class BookmarkType = LONG,
   class BookmarkMapClass = CAtlMap < RowClass::KeyType, RowClass* >>
class ATL_NO_VTABLE IRowsetLocateImpl : public IRowsetImpl<
       T,
       RowsetInterface,
       RowClass,
       MapClass>
```

### <a name="parameters"></a>Parametry

*&*<br/>
Klasa pochodna `IRowsetLocateImpl`.

*RowsetInterface*<br/>
Klasa pochodna `IRowsetImpl`.

*RowClass*<br/>
Jednostka magazynowa dla `HROW`.

*MapClass*<br/>
Jednostka magazynowa dla wszystkich dojść wiersza przechowywanych przez dostawcę.

*BookmarkKeyType*<br/>
Typ zakładki, na przykład LONG lub String. Zwykłe zakładki muszą mieć długość co najmniej dwóch bajtów. (Długość jednobajtowa jest zastrzeżona dla OLE DB [zakładki standardowe](/previous-versions/windows/desktop/ms712954(v=vs.85))`DBBMK_FIRST`, `DBBMK_LAST`i `DBBMK_INVALID`).

*Zakładka*<br/>
Mechanizm mapowania do obsługi relacji między zakładkami a danymi.

*BookmarkMapClass*<br/>
Jednostka magazynowa dla wszystkich dojść wiersza przechowywanych przez zakładkę.

## <a name="requirements"></a>Wymagania

**Nagłówek**: ATLDB. h

## <a name="members"></a>Members

### <a name="interface-methods"></a>Metody interfejsu

|||
|-|-|
|[Compare](#compare)|Porównuje dwie zakładki.|
|[GetRowsAt](#getrowsat)|Pobiera wiersze zaczynające się od wiersza określonego przez przesunięcie od zakładki.|
|[GetRowsByBookmark](#getrowsbybookmark)|Pobiera wiersze zgodne z określonymi zakładkami.|
|[Skrótu](#hash)|Zwraca wartości skrótu dla określonych zakładek.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|[m_rgBookmarks](#rgbookmarks)|Tablica zakładek.|

## <a name="remarks"></a>Uwagi

`IRowsetLocateImpl` jest implementacją szablonów OLE DB interfejsu [IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85)) . `IRowsetLocate` służy do pobierania dowolnych wierszy z zestawu wierszy. Zestaw wierszy, który nie implementuje tego interfejsu, jest zestawem wierszy `sequential`. Gdy `IRowsetLocate` jest obecny w zestawie wierszy, kolumna 0 jest zakładką wierszy; odczytanie tej kolumny spowoduje uzyskanie wartości zakładki, której można użyć do zmiany położenia do tego samego wiersza.

`IRowsetLocateImpl` służy do implementowania obsługi zakładki w dostawcach. Zakładki są symbolami zastępczymi (indeksami w zestawie wierszy), które umożliwiają konsumentom szybkie zwracanie do wiersza, co pozwala na szybki dostęp do danych. Dostawca określa, jakie zakładki mogą jednoznacznie identyfikować wiersz. Przy użyciu metod `IRowsetLocateImpl` można porównać zakładki, pobierać wiersze według przesunięcia, pobierać wiersze według zakładki i zwracać wartości skrótów dla zakładek.

Aby można było obsługiwać zakładki OLE DB w zestawie wierszy, należy uczynić zestaw wierszy Dziedziczony z tej klasy.

Aby uzyskać informacje na temat implementowania obsługi zakładek, zobacz [Obsługa dostawcy dla zakładek](../../data/oledb/provider-support-for-bookmarks.md) w przewodniku i [zakładkach](/previous-versions/windows/desktop/ms709728(v=vs.85)) programu  *C++ Visual programisty* w zestawie SDK platformy *OLE DB programisty* .

## <a name="irowsetlocateimplcompare"></a><a name="compare"></a>IRowsetLocateImpl:: Compare

Porównuje dwie zakładki.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (Compare )(HCHAPTER /* hReserved */,
   DBBKMARK cbBookmark1,
   const BYTE* pBookmark1,
   DBBKMARK cbBookmark2,
   const BYTE* pBookmark2,
   DBCOMPARE* pComparison);
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowsetLocate:: Compare](/previous-versions/windows/desktop/ms709539(v=vs.85)) w *dokumentacji programisty OLE DB*.

### <a name="remarks"></a>Uwagi

Każda z tych zakładek może być standardową [zakładką w standardowej](/previous-versions/windows/desktop/ms712954(v=vs.85)) OLE DB (`DBBMK_FIRST`, `DBBMK_LAST`lub `DBBMK_INVALID`). Wartość zwracana w `pComparison` określa relację między dwiema zakładkami:

- DBCOMPARE_LT (`cbBookmark1` przed `cbBookmark2`.)

- DBCOMPARE_EQ (`cbBookmark1` jest równa `cbBookmark2`.)

- DBCOMPARE_GT (`cbBookmark1` jest po `cbBookmark2`.)

- DBCOMPARE_NE (zakładki są równe i nie są uporządkowane).

- DBCOMPARE_NOTCOMPARABLE (nie można porównać zakładek).

## <a name="irowsetlocateimplgetrowsat"></a><a name="getrowsat"></a>IRowsetLocateImpl:: GetRowsAt

Pobiera wiersze zaczynające się od wiersza określonego przez przesunięcie od zakładki.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (GetRowsAt )(HWATCHREGION /* hReserved1 */,
   HCHAPTER hReserved2,
   DBBKMARK cbBookmark,
   const BYTE* pBookmark,
   DBROWOFFSET lRowsOffset,
   DBROWCOUNT cRows,
   DBCOUNTITEM* pcRowsObtained,
   HROW** prghRows);
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowsetLocate:: GetRowsAt](/previous-versions/windows/desktop/ms723031(v=vs.85)) w *dokumentacji programisty OLE DB*.

### <a name="remarks"></a>Uwagi

Aby zamiast tego pobrać z pozycji kursora, użyj [IRowset:: GetRowsAt](/previous-versions/windows/desktop/ms723031(v=vs.85)).

`IRowsetLocateImpl::GetRowsAt` nie zmienia położenia kursora.

## <a name="irowsetlocateimplgetrowsbybookmark"></a><a name="getrowsbybookmark"></a>IRowsetLocateImpl:: GetRowsByBookmark

Pobiera jeden lub więcej wierszy, które pasują do określonych zakładek.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (GetRowsByBookmark )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const DBBKMARK rgcbBookmarks[],
   const BYTE* rgpBookmarks,
   HROW rghRows[],
   DBROWSTATUS* rgRowStatus[]);
```

#### <a name="parameters"></a>Parametry

*hReserved*<br/>
podczas Odpowiada parametrowi *hChapter* do [IRowsetLocate:: GetRowsByBookmark](/previous-versions/windows/desktop/ms725420(v=vs.85)).

W przypadku innych parametrów, zobacz [IRowsetLocate:: GetRowsByBookmark](/previous-versions/windows/desktop/ms725420(v=vs.85)) w *dokumentacji programisty OLE DB*.

### <a name="remarks"></a>Uwagi

Zakładka może być zdefiniowaną wartością lub OLE DB [zakładkami standardowymi](/previous-versions/windows/desktop/ms712954(v=vs.85)) (`DBBMK_FIRST` lub `DBBMK_LAST`). Nie zmienia położenia kursora.

## <a name="irowsetlocateimplhash"></a><a name="hash"></a>IRowsetLocateImpl:: hash

Zwraca wartości skrótu dla określonych zakładek.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (Hash )(HCHAPTER /* hReserved */,
   DBBKMARK cbBookmarks,
   const DBBKMARK* rgcbBookmarks[],
   const BYTE* rgpBookmarks[],
   DBHASHVALUE rgHashValues[],
   DBROWSTATUS rgBookmarkStatus[]);
```

#### <a name="parameters"></a>Parametry

*hReserved*<br/>
podczas Odpowiada parametrowi *hChapter* do [IRowsetLocate:: hash](/previous-versions/windows/desktop/ms709697(v=vs.85)).

Aby poznać inne parametry, zobacz [IRowsetLocate:: hash](/previous-versions/windows/desktop/ms709697(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="irowsetlocateimplm_rgbookmarks"></a><a name="rgbookmarks"></a>IRowsetLocateImpl:: m_rgBookmarks

Tablica zakładek.

### <a name="syntax"></a>Składnia

```cpp
CAtlArray<DBROWCOUNT> m_rgBookmarks;
```

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[IRowsetLocate:](/previous-versions/windows/desktop/ms721190(v=vs.85))
IRowset [obsługa dostawców dla zakładek](../../data/oledb/provider-support-for-bookmarks.md)<br/>
[Zakładki](/previous-versions/windows/desktop/ms709728(v=vs.85))
