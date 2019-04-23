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
ms.openlocfilehash: e3513084697a60a33b9fa2ab02222a9b332cce79
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039822"
---
# <a name="irowsetlocateimpl-class"></a>IRowsetLocateImpl — Klasa

Implementuje OLE DB [irowsetlocate —](/previous-versions/windows/desktop/ms721190(v=vs.85)) interfejs, który pobiera wiersze z dowolnego z zestawu wierszy.

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

*T*<br/>
Klasa pochodząca z `IRowsetLocateImpl`.

*RowsetInterface*<br/>
Klasa pochodząca z `IRowsetImpl`.

*RowClass*<br/>
Jednostki magazynu na potrzeby `HROW`.

*MapClass*<br/>
Jednostki magazynu na potrzeby wszystkich dojść do wierszy są przechowywane przez dostawcę.

*BookmarkKeyType*<br/>
Typ zakładki, takie jak DŁUGA lub ciąg. Zwykłe zakładki musi mieć długość co najmniej dwa bajty. (Pojedynczych bajtów długości jest zarezerwowany dla OLE DB [standardowa zakładki](/previous-versions/windows/desktop/ms712954(v=vs.85))`DBBMK_FIRST`, `DBBMK_LAST`, i `DBBMK_INVALID`.)

*BookmarkType*<br/>
Mechanizm mapowania dotyczące utrzymania relacji zakładki do danych.

*BookmarkMapClass*<br/>
Jednostki magazynu na potrzeby wszystkich dojść do wierszy w posiadaniu zakładki.

## <a name="requirements"></a>Wymagania

**Nagłówek**: atldb.h

## <a name="members"></a>Elementy członkowskie

### <a name="interface-methods"></a>Metody interfejsu

|||
|-|-|
|[Compare](#compare)|Porównuje dwa zakładek.|
|[GetRowsAt](#getrowsat)|Pobiera wiersze, rozpoczynając od wiersza określonego przez przesunięcie od zakładki.|
|[GetRowsByBookmark](#getrowsbybookmark)|Pobiera wiersze, które odpowiadają określonej zakładki.|
|[Skrót](#hash)|Zwraca wartość skrótu wartości dla określonego zakładek.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|[m_rgBookmarks](#rgbookmarks)|Tablica zakładek.|

## <a name="remarks"></a>Uwagi

`IRowsetLocateImpl` jest to implementacja szablony OLE DB [irowsetlocate —](/previous-versions/windows/desktop/ms721190(v=vs.85)) interfejsu. `IRowsetLocate` Służy do pobrania dowolnych wierszy w zestawie wierszy. Zestaw wierszy, który nie implementuje ten interfejs jest `sequential` zestawu wierszy. Gdy `IRowsetLocate` jest obecny w zestawie wierszy, kolumny 0 jest zakładki dla wierszy; odczytu w tej kolumnie osiągnie wartość zakładki, który może służyć do zmiany położenia na tym samym wierszu.

`IRowsetLocateImpl` Służy do implementowania Obsługa zakładek w dostawcy. Zakładki są symbolami zastępczymi (indeksów w zestawie wierszy), które umożliwiają odbiorcę, aby szybko powrócić do wiersza, umożliwiające szybki dostęp do danych. Określa dostawcę, co zakładek może jednoznacznie zidentyfikować wiersz. Za pomocą `IRowsetLocateImpl` metod, można porównać zakładek, wiersze pobierania przez przesunięcie zakładki, wierszy i pobierania i zwracania wartości skrótów dla zakładek.

Aby zapewnić obsługę OLE DB zakładki w zestawie wierszy, należy pochodne względem tej klasy zestawu wierszy.

Aby uzyskać informacji dotyczących implementowania Obsługa zakładek, zobacz [dostawca obsługuje dla zakładek](../../data/oledb/provider-support-for-bookmarks.md) w *Visual C++ przewodnik* i [zakładki](/previous-versions/windows/desktop/ms709728(v=vs.85)) w *OLE DB Podręcznik programisty* w zestaw SDK platformy.

## <a name="compare"></a> IRowsetLocateImpl::Compare

Porównuje dwa zakładek.

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

Zobacz [IRowsetLocate::Compare](/previous-versions/windows/desktop/ms709539(v=vs.85)) w *OLE DB Podręcznik programisty*.

### <a name="remarks"></a>Uwagi

Jedną z zakładek może być standardowego zdefiniowane OLE DB [standardowa zakładki](/previous-versions/windows/desktop/ms712954(v=vs.85)) (`DBBMK_FIRST`, `DBBMK_LAST`, lub `DBBMK_INVALID`). Wartość zwracana w `pComparison` określa relację pomiędzy dwoma zakładek:

- DBCOMPARE_LT (`cbBookmark1` przed `cbBookmark2`.)

- DBCOMPARE_EQ (`cbBookmark1` jest równa `cbBookmark2`.)

- DBCOMPARE_GT (`cbBookmark1` po `cbBookmark2`.)

- DBCOMPARE_NE (zakładki są równe i nie uporządkowanych).

- DBCOMPARE_NOTCOMPARABLE (nie można porównać zakładek.)

## <a name="getrowsat"></a> IRowsetLocateImpl::GetRowsAt

Pobiera wiersze, rozpoczynając od wiersza określonego przez przesunięcie od zakładki.

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

Zobacz [IRowsetLocate::GetRowsAt](/previous-versions/windows/desktop/ms723031(v=vs.85)) w *OLE DB Podręcznik programisty*.

### <a name="remarks"></a>Uwagi

Fetch od pozycji kursora zamiast tego użyj [IRowset::GetRowsAt](/previous-versions/windows/desktop/ms723031(v=vs.85)).

`IRowsetLocateImpl::GetRowsAt` nie zmienia pozycji kursora.

## <a name="getrowsbybookmark"></a> IRowsetLocateImpl::GetRowsByBookmark

Pobiera jeden lub więcej wierszy, które odpowiadają określonej zakładki.

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
[in] Odnosi się do *hChapter* parametr [IRowsetLocate::GetRowsByBookmark](/previous-versions/windows/desktop/ms725420(v=vs.85)).

Dla innych parametrów, zobacz [IRowsetLocate::GetRowsByBookmark](/previous-versions/windows/desktop/ms725420(v=vs.85)) w *OLE DB Podręcznik programisty*.

### <a name="remarks"></a>Uwagi

Zakładki może być wartością zdefiniujesz lub OLE DB [standardowa zakładki](/previous-versions/windows/desktop/ms712954(v=vs.85)) (`DBBMK_FIRST` lub `DBBMK_LAST`). nie zmienia pozycji kursora.

## <a name="hash"></a> IRowsetLocateImpl::Hash

Zwraca wartość skrótu wartości dla określonego zakładek.

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
[in] Odnosi się do *hChapter* parametr [IRowsetLocate::Hash](/previous-versions/windows/desktop/ms709697(v=vs.85)).

Dla innych parametrów, zobacz [IRowsetLocate::Hash](/previous-versions/windows/desktop/ms709697(v=vs.85)) w *OLE DB Podręcznik programisty*.

## <a name="rgbookmarks"></a> IRowsetLocateImpl::m_rgBookmarks

Tablica zakładek.

### <a name="syntax"></a>Składnia

```cpp
CAtlArray<DBROWCOUNT> m_rgBookmarks;
```

## <a name="see-also"></a>Zobacz także

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[IRowsetLocate:IRowset](/previous-versions/windows/desktop/ms721190(v=vs.85))
[Obsługa dostawców dla zakładek](../../data/oledb/provider-support-for-bookmarks.md)<br/>
[Zakładki](/previous-versions/windows/desktop/ms709728(v=vs.85))