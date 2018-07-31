---
title: Irowsetimpl — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetImpl
- IRowsetImpl::AddRefRows
- AddRefRows
- IRowsetImpl.AddRefRows
- ATL::IRowsetImpl::AddRefRows
- ATL.IRowsetImpl.AddRefRows
- IRowsetImpl.CreateRow
- ATL.IRowsetImpl.CreateRow
- ATL::IRowsetImpl::CreateRow
- CreateRow
- IRowsetImpl::CreateRow
- ATL.IRowsetImpl.GetData
- ATL::IRowsetImpl::GetData
- IRowsetImpl::GetData
- IRowsetImpl.GetData
- GetDBStatus
- IRowsetImpl.GetDBStatus
- IRowsetImpl::GetDBStatus
- GetNextRows
- ATL.IRowsetImpl.GetNextRows
- ATL::IRowsetImpl::GetNextRows
- IRowsetImpl::GetNextRows
- IRowsetImpl.GetNextRows
- IRowsetImpl.IRowsetImpl
- ATL::IRowsetImpl::IRowsetImpl
- ATL.IRowsetImpl.IRowsetImpl
- IRowsetImpl::IRowsetImpl
- IRowsetImpl
- ATL::IRowsetImpl::RefRows
- ATL.IRowsetImpl.RefRows
- IRowsetImpl.RefRows
- RefRows
- IRowsetImpl::RefRows
- ATL.IRowsetImpl.ReleaseRows
- ReleaseRows
- IRowsetImpl::ReleaseRows
- ATL::IRowsetImpl::ReleaseRows
- IRowsetImpl.ReleaseRows
- ATL.IRowsetImpl.RestartPosition
- IRowsetImpl::RestartPosition
- RestartPosition
- ATL::IRowsetImpl::RestartPosition
- IRowsetImpl.RestartPosition
- IRowsetImpl.SetDBStatus
- IRowsetImpl::SetDBStatus
- SetDBStatus
- ATL.IRowsetImpl.m_bCanFetchBack
- ATL::IRowsetImpl::m_bCanFetchBack
- IRowsetImpl.m_bCanFetchBack
- IRowsetImpl::m_bCanFetchBack
- m_bCanFetchBack
- IRowsetImpl::m_bCanScrollBack
- ATL::IRowsetImpl::m_bCanScrollBack
- IRowsetImpl.m_bCanScrollBack
- ATL.IRowsetImpl.m_bCanScrollBack
- m_bCanScrollBack
- ATL.IRowsetImpl.m_bReset
- IRowsetImpl.m_bReset
- m_bReset
- IRowsetImpl::m_bReset
- ATL::IRowsetImpl::m_bReset
- IRowsetImpl::m_iRowset
- IRowsetImpl.m_iRowset
- ATL::IRowsetImpl::m_iRowset
- ATL.IRowsetImpl.m_iRowset
- m_iRowset
- IRowsetImpl::m_rgRowHandles
- IRowsetImpl.m_rgRowHandles
- m_rgRowHandles
- ATL::IRowsetImpl::m_rgRowHandles
- ATL.IRowsetImpl.m_rgRowHandles
dev_langs:
- C++
helpviewer_keywords:
- IRowsetImpl class
- AddRefRows method
- CreateRow method
- GetData method [OLE DB]
- GetDBStatus method
- GetNextRows method
- IRowsetImpl constructor
- RefRows method
- ReleaseRows method
- RestartPosition method
- SetDBStatus method
- m_bCanFetchBack
- m_bCanScrollBack
- m_bReset
- m_iRowset
- m_rgRowHandles
ms.assetid: 6a9189af-7556-45b1-adcb-9d62bb36704c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6cd6ec4bcee26c1e2fb558670c69d0130808c933
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2018
ms.locfileid: "39338343"
---
# <a name="irowsetimpl-class"></a>IRowsetImpl — Klasa
Udostępnia implementację `IRowset` interfejsu.  
  
## <a name="syntax"></a>Składnia

```cpp
template <  
   class T,   
   class RowsetInterface,  
   class RowClass = CSimpleRow,  
   class MapClass = CAtlMap <  
      RowClass::KeyType,  
      RowClass*>>  
class ATL_NO_VTABLE IRowsetImpl : public RowsetInterface  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Z klasą pochodną `IRowsetImpl`.  
  
 *RowsetInterface*  
 Klasa pochodząca z `IRowsetImpl`.  
  
 *RowClass*  
 Jednostki magazynu na potrzeby `HROW`.  
  
 *MapClass*  
 Jednostki magazynu na potrzeby wszystkich dojść do wierszy są przechowywane przez dostawcę.  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Addrefrows —](#addrefrows)|Dodaje licznik odwołań do istniejących uchwyt wiersza.|  
|[Createrow —](#createrow)|Wywoływane przez [getnextrows —](../../data/oledb/irowsetimpl-getnextrows.md) można przydzielić nowego `HROW`. Nie jest wywoływana bezpośrednio przez użytkownika.|  
|[GetData](#getdata)|Pobiera dane z zestawu wierszy kopię wiersza.|  
|[Getdbstatus —](#getdbstatus)|Zwraca stan dla określonego pola.|  
|[Getnextrows —](#getnextrows)|Pobiera wiersze po kolei, uzupełnij poprzedniej pozycji.|  
|[Irowsetimpl —](#irowsetimpl)|Konstruktor. Nie jest wywoływana bezpośrednio przez użytkownika.|  
|[Refrows —](#refrows)|Wywoływane przez [addrefrows —](../../data/oledb/irowsetimpl-addrefrows.md) i [releaserows —](../../data/oledb/irowsetimpl-releaserows.md). Nie jest wywoływana bezpośrednio przez użytkownika.|  
|[Releaserows —](#releaserows)|Wersje wierszy.|  
|[Operacja restartposition wykonywana](#restartposition)|Powoduje przeniesienie pozycji następnego pobierania na jego początkowe położenie; oznacza to utworzyć jego położenie podczas pierwszego zestawu wierszy.|  
|[Setdbstatus —](#setdbstatus)|Ustawia flagi stanu dla określonego pola.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|||  
|-|-|  
|[m_bCanFetchBack](#bcanfetchback)|Wskazuje, czy dostawca obsługuje pobieranie z poprzednimi wersjami.|  
|[m_bCanScrollBack](#bcanscrollback)|Wskazuje, czy dostawca może mieć wstecz jego przewijania kursora.|  
|[m_bReset](#breset)|Wskazuje, czy dostawca został zresetowany jego pozycja kursora. Ma specjalne znaczenie, gdy przewijanie do tyłu lub pobieranie wstecz w [getnextrows —](../../data/oledb/irowsetimpl-getnextrows.md).|  
|[m_iRowset](#irowset)|Indeks wierszy, reprezentujący kursora.|  
|[m_rgRowHandles](#rgrowhandles)|Lista dojść do wierszy.|  
  
## <a name="remarks"></a>Uwagi  
 [IRowset](https://msdn.microsoft.com/library/ms720986.aspx) jest interfejsem podstawowy zestaw wierszy.  

## <a name="addrefrows"></a> IRowsetImpl::AddRefRows
Dodaje licznik odwołań do istniejących uchwyt wiersza.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
STDMETHOD(AddRefRows )(DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBREFCOUNT rgRefCounts[],  
   DBROWSTATUS rgRowStatus[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IRowset::AddRefRows](https://msdn.microsoft.com/library/ms719619.aspx) w *OLE DB Podręcznik programisty*.  

## <a name="createrow"></a> IRowsetImpl::CreateRow
Wywoływane przez metody pomocnika [getnextrows —](../../data/oledb/irowsetimpl-getnextrows.md) można przydzielić nowego `HROW`.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT CreateRow(DBROWOFFSET lRowsOffset,  
   DBCOUNTITEM& cRowsObtained,  
   HROW* rgRows);  
```  
  
#### <a name="parameters"></a>Parametry  
 *lRowsOffset*  
 Pozycja kursora wiersza tworzona.  
  
 *cRowsObtained*  
 Odwołanie przekazywany z powrotem do użytkownika, określającą liczbę wierszy, utworzony.  
  
 *rgRows*  
 Tablica `HROW`s zwracane do obiektu wywołującego za pomocą dojścia do nowo utworzonego wierszy.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wiersz istnieje, ta metoda wywołuje [addrefrows —](../../data/oledb/irowsetimpl-addrefrows.md) i zwraca. W przeciwnym razie przydziela nowe wystąpienie klasy zmiennej szablonu RowClass i dodaje go do [m_rgRowHandles](../../data/oledb/irowsetimpl-m-rgrowhandles.md).  
  
## <a name="getdata"></a> IRowsetImpl::GetData
Pobiera dane z zestawu wierszy kopię wiersza.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
STDMETHOD(GetData )(HROW hRow,  
   HACCESSOR hAccessor,  
   void* pDstData);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IRowset::GetData](https://msdn.microsoft.com/library/ms716988.aspx) w *OLE DB Podręcznik programisty*.  
  
 Niektóre parametry odpowiadają *OLE DB Podręcznik programisty* parametry różnych nazw, które są opisane w `IRowset::GetData`:  
  
|Parametry szablonu OLE DB|*OLE DB Podręcznik programisty* parametrów|  
|--------------------------------|------------------------------------------------|  
|*pDstData*|*pData*|  
  
### <a name="remarks"></a>Uwagi  
 Obsługuje także konwersja danych za pomocą konwersji danych OLE DB biblioteki DLL. 

## <a name="getdbstatus"></a> IRowsetImpl::GetDBStatus
Zwraca stan DBSTATUS flagi dla określonego pola.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
virtual DBSTATUS GetDBStatus(RowClass* currentRow,  
   ATLCOLUMNINFO* columnNames);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] *TableRow*  
 Bieżący wiersz.  
  
 [in] *columnNames*  
 Kolumna, dla którego wnioskuje się stan.  
  
### <a name="return-value"></a>Wartość zwracana  
 [DBSTATUS](https://msdn.microsoft.com/library/ms722617.aspx) flagi dla kolumny. 

## <a name="getnextrows"></a> IRowsetImpl::GetNextRows
Pobiera wiersze po kolei, uzupełnij poprzedniej pozycji.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
STDMETHOD(GetNextRows )(HCHAPTER hReserved,  
   DBROWOFFSET lRowsOffset,  
   DBROWCOUNT cRows,  
   DBCOUNTITEM* pcRowsObtained,  
   HROW** prghRows);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IRowset::GetNextRows](https://msdn.microsoft.com/library/ms709827.aspx) w *OLE DB Podręcznik programisty*. 

## <a name="irowsetimpl"></a> IRowsetImpl::IRowsetImpl
Konstruktor.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
IRowsetImpl();  
```  
  
### <a name="remarks"></a>Uwagi  
 Zazwyczaj nie trzeba bezpośrednio wywołać tę metodę.  

## <a name="refrows"></a> IRowsetImpl::RefRows
Wywoływane przez [addrefrows —](../../data/oledb/irowsetimpl-addrefrows.md) i [releaserows —](../../data/oledb/irowsetimpl-releaserows.md) Zwiększ lub wersji licznika odwołań do istniejących uchwyt wiersza.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT RefRows(DBCOUNTITEM cRows,  
   const HROWrghRows[],  
   DBREFCOUNT rgRefCounts[],  
   DBROWSTATUS rgRowStatus[],  
   BOOL bAdd);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IRowset::AddRefRows](https://msdn.microsoft.com/library/ms719619.aspx) w *OLE DB Podręcznik programisty*.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowe wartości HRESULT.  

## <a name="releaserows"></a> IRowsetImpl::ReleaseRows
Wersje wierszy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
STDMETHOD(ReleaseRows )(DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBROWOPTIONS rgRowOptions[],  
   DBREFCOUNT rgRefCounts[],  
   DBROWSTATUS rgRowStatus[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IRowset::ReleaseRows](https://msdn.microsoft.com/library/ms719771.aspx) w *OLE DB Podręcznik programisty*.  

## <a name="restartposition"></a> IRowsetImpl::RestartPosition
Powoduje przeniesienie pozycji następnego pobierania na jego początkowe położenie; oznacza to utworzyć jego położenie podczas pierwszego zestawu wierszy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
STDMETHOD(RestartPosition )(HCHAPTER /* hReserved */);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IRowset::RestartPosition](https://msdn.microsoft.com/library/ms712877.aspx) w *OLE DB Podręcznik programisty*.  
  
### <a name="remarks"></a>Uwagi  
 Pozycja zestawu wierszy jest niezdefiniowane, aż do `GetNextRow` jest wywoływana. Możesz przenosić Wstecz w rowet przez wywołanie metody `RestartPosition` i pobieranie lub przewijanie do tyłu.  

## <a name="setdbstatus"></a> IRowsetImpl::SetDBStatus
Ustawia flagi stanu DBSTATUS dla określonego pola.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
virtual HRESULT SetDBStatus(DBSTATUS* statusFlags,  
   RowClass* currentRow,  
   ATLCOLUMNINFO* columnInfo);  
```  
  
#### <a name="parameters"></a>Parametry  
 *statusFlags*  
 [DBSTATUS](https://msdn.microsoft.com/library/ms722617.aspx) flagi, aby określić dla kolumny.  
  
 *TableRow*  
 Bieżący wiersz.  
  
 *columnInfo*  
 Kolumna, dla którego stan jest ustawiony.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowe wartości HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Dostawca zastępuje tę funkcję, aby zapewnić przetwarzana w specjalny DBSTATUS_S_ISNULL i DBSTATUS_S_DEFAULT. 

## <a name="bcanfetchback"></a> IRowsetImpl::m_bCanFetchBack
Wskazuje, czy dostawca obsługuje pobieranie z poprzednimi wersjami.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
unsigned m_bCanFetchBack:1;  
```  
  
### <a name="remarks"></a>Uwagi  
 Połączone `DBPROP_CANFETCHBACKWARDS` właściwość `DBPROPSET_ROWSET` grupy. Dostawca musi obsługiwać `DBPROP_CANFETCHBACKWARDS` dla `m_bCanFetchBackwards` jako **true**.  

## <a name="bcanscrollback"></a> IRowsetImpl::m_bCanScrollBack
Wskazuje, czy dostawca może mieć wstecz jego przewijania kursora.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
unsigned  m_bCanScrollBack:1;  
```  
  
### <a name="remarks"></a>Uwagi  
 Połączone `DBPROP_CANSCROLLBACKWARDS` właściwość `DBPROPSET_ROWSET` grupy. Dostawca musi obsługiwać `DBPROP_CANSCROLLBACKWARDS` dla `m_bCanFetchBackwards` jako **true**. 

## <a name="breset"></a> IRowsetImpl::m_bReset
Flagi bitowe używane do określania, jeśli pozycja kursora jest zdefiniowany w zestawie wierszy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
unsigned m_bReset:1;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli użytkownik wywołuje [getnextrows —](../../data/oledb/irowsetimpl-getnextrows.md) przy użyciu ujemnych `lOffset` lub *cRows* i `m_bReset` ma wartość true, `GetNextRows` przenosi koniec zestawu wierszy. Jeśli `m_bReset` ma wartość FAŁSZ, użytkownik otrzymuje zwróciło kod błędu zgodnie ze specyfikacją OLE DB. `m_bReset` Flaga jest ustawiona na **true** po pierwszym utworzeniu zestawu wierszy, a kiedy użytkownik wywołuje [IRowsetImpl::RestartPosition](../../data/oledb/irowsetimpl-restartposition.md). Pobiera równa **false** podczas wywoływania `GetNextRows`. 

## <a name="irowset"></a> IRowsetImpl::m_iRowset
Indeks wierszy, reprezentujący kursora.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
DBROWOFFSET m_iRowset;  
```  

## <a name="rgrowhandles"></a> IRowsetImpl::m_rgRowHandles
Mapy uchwytów wierszy, które aktualnie znajdujących się przez dostawcę w odpowiedzi na `GetNextRows`.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
MapClass m_rgRowHandles;  
```  
  
### <a name="remarks"></a>Uwagi  
 Dojść do wierszy są usuwane przez wywołanie metody `ReleaseRows`. Zobacz [irowsetimpl — omówienie](../../data/oledb/irowsetimpl-class.md) dla definicji *MapClass*.  

## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)    
 [CSimpleRow, klasa](../../data/oledb/csimplerow-class.md)