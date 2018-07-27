---
title: Irowsetlocateimpl — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 986626fa391971ce342f8d80b9e3e7f8ec979b63
ms.sourcegitcommit: e5792fcb89b9ba64c401f90f4f26a8e45d4a2359
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2018
ms.locfileid: "39322179"
---
# <a name="irowsetlocateimpl-class"></a>IRowsetLocateImpl — Klasa
Implementuje OLE DB [irowsetlocate —](https://msdn.microsoft.com/library/ms721190.aspx) interfejs, który pobiera wiersze z dowolnego z zestawu wierszy.  
  
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
 *T*  
 Klasa pochodząca z `IRowsetLocateImpl`.  
  
 *RowsetInterface*  
 Klasa pochodząca z `IRowsetImpl`.  
  
 *RowClass*  
 Jednostki magazynu na potrzeby `HROW`.  
  
 *MapClass*  
 Jednostki magazynu na potrzeby wszystkich dojść do wierszy są przechowywane przez dostawcę.  
  
 *BookmarkKeyType*  
 Typ zakładki, takie jak DŁUGA lub ciąg. Zwykłe zakładki musi mieć długość co najmniej dwa bajty. (Pojedynczych bajtów długości jest zarezerwowany dla OLE DB [standardowa zakładki](https://msdn.microsoft.com/library/ms712954.aspx)`DBBMK_FIRST`, `DBBMK_LAST`, i `DBBMK_INVALID`.)  
  
 *BookmarkType*  
 Mechanizm mapowania dotyczące utrzymania relacji zakładki do danych.  
  
 *BookmarkMapClass*  
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
 `IRowsetLocateImpl` jest to implementacja szablony OLE DB [irowsetlocate —](https://msdn.microsoft.com/library/ms721190.aspx) interfejsu. `IRowsetLocate` Służy do pobrania dowolnych wierszy w zestawie wierszy. Zestaw wierszy, który nie implementuje ten interfejs jest `sequential` zestawu wierszy. Gdy `IRowsetLocate` jest obecny w zestawie wierszy, kolumny 0 jest zakładki dla wierszy; odczytu w tej kolumnie osiągnie wartość zakładki, który może służyć do zmiany położenia na tym samym wierszu.  
  
 `IRowsetLocateImpl` Służy do implementowania Obsługa zakładek w dostawcy. Zakładki są symbolami zastępczymi (indeksów w zestawie wierszy), które umożliwiają odbiorcę, aby szybko powrócić do wiersza, umożliwiające szybki dostęp do danych. Określa dostawcę, co zakładek może jednoznacznie zidentyfikować wiersz. Za pomocą `IRowsetLocateImpl` metod, można porównać zakładek, wiersze pobierania przez przesunięcie zakładki, wierszy i pobierania i zwracania wartości skrótów dla zakładek.  
  
 Aby zapewnić obsługę OLE DB zakładki w zestawie wierszy, należy pochodne względem tej klasy zestawu wierszy.  
  
 Aby uzyskać informacji dotyczących implementowania Obsługa zakładek, zobacz [dostawca obsługuje dla zakładek](../../data/oledb/provider-support-for-bookmarks.md) w *Visual C++ przewodnik* i [zakładki](https://msdn.microsoft.com/library/ms709728.aspx) w *OLE DB Podręcznik programisty* w zestaw SDK platformy.  

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
 Zobacz [IRowsetLocate::Compare](https://msdn.microsoft.com/library/ms709539.aspx) w *OLE DB Podręcznik programisty*.  
  
### <a name="remarks"></a>Uwagi  
 Jedną z zakładek może być standardowego zdefiniowane OLE DB [standardowa zakładki](https://msdn.microsoft.com/library/ms712954.aspx) (`DBBMK_FIRST`, `DBBMK_LAST`, lub `DBBMK_INVALID`). Wartość zwracana w `pComparison` określa relację pomiędzy dwoma zakładek:  
  
-   DBCOMPARE_LT (`cbBookmark1` przed `cbBookmark2`.)  
  
-   DBCOMPARE_EQ (`cbBookmark1` jest równa `cbBookmark2`.)  
  
-   DBCOMPARE_GT (`cbBookmark1` po `cbBookmark2`.)  
  
-   DBCOMPARE_NE (zakładki są równe i nie uporządkowanych).  
  
-   DBCOMPARE_NOTCOMPARABLE (nie można porównać zakładek.) 

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
 Zobacz [IRowsetLocate::GetRowsAt](https://msdn.microsoft.com/library/ms723031.aspx) w *OLE DB Podręcznik programisty*.  
  
### <a name="remarks"></a>Uwagi  
 Fetch od pozycji kursora zamiast tego użyj [IRowset::GetRowsAt](https://msdn.microsoft.com/library/ms723031.aspx).  
  
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
 *hReserved*  
 [in] Odnosi się do *hChapter* parametr [IRowsetLocate::GetRowsByBookmark](https://msdn.microsoft.com/library/ms725420.aspx).  
  
 Dla innych parametrów, zobacz [IRowsetLocate::GetRowsByBookmark](https://msdn.microsoft.com/library/ms725420.aspx) w *OLE DB Podręcznik programisty*.  
  
### <a name="remarks"></a>Uwagi  
 Zakładki może być wartością zdefiniujesz lub OLE DB [standardowa zakładki](https://msdn.microsoft.com/library/ms712954.aspx) (`DBBMK_FIRST` lub `DBBMK_LAST`). Nie zmienia pozycji kursora.  

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
 *hReserved*  
 [in] Odnosi się do *hChapter* parametr [IRowsetLocate::Hash](https://msdn.microsoft.com/library/ms709697.aspx).  
  
 Dla innych parametrów, zobacz [IRowsetLocate::Hash](https://msdn.microsoft.com/library/ms709697.aspx) w *OLE DB Podręcznik programisty*.  

## <a name="rgbookmarks"></a> IRowsetLocateImpl::m_rgBookmarks
Tablica zakładek.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
CAtlArray<DBROWCOUNT> m_rgBookmarks;  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [IRowsetLocate:IRowset](https://msdn.microsoft.com/library/ms721190.aspx)   
 [Obsługa dostawców dla zakładek](../../data/oledb/provider-support-for-bookmarks.md)   
 [Zakładki](https://msdn.microsoft.com/library/ms709728.aspx)
