---
title: Irowsetchangeimpl — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IRowsetChangeImpl
- IRowsetChangeImpl
- ATL.IRowsetChangeImpl
- ATL.IRowsetChangeImpl.DeleteRows
- ATL::IRowsetChangeImpl::DeleteRows
- IRowsetChangeImpl.DeleteRows
- DeleteRows
- IRowsetChangeImpl::DeleteRows
- ATL.IRowsetChangeImpl.InsertRow
- InsertRow
- IRowsetChangeImpl.InsertRow
- ATL::IRowsetChangeImpl::InsertRow
- IRowsetChangeImpl::InsertRow
- SetData
- IRowsetChangeImpl::SetData
- ATL.IRowsetChangeImpl.SetData
- IRowsetChangeImpl.SetData
- ATL::IRowsetChangeImpl::SetData
- IRowsetChangeImpl::FlushData
- IRowsetChangeImpl.FlushData
- FlushData
dev_langs:
- C++
helpviewer_keywords:
- providers, updatable
- updatable providers, immediate update
- IRowsetChangeImpl class
- DeleteRows method
- InsertRow method
- SetData method
- FlushData method
ms.assetid: 1e9fee15-ed9e-4387-af8f-215569beca6c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e0ee351771d56b417396583ef41a96c62ff6bafd
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2018
ms.locfileid: "49082530"
---
# <a name="irowsetchangeimpl-class"></a>IRowsetChangeImpl — Klasa

Szablony OLE DB implementacji [IRowsetChange](/previous-versions/windows/desktop/ms715790) interfejsu w specyfikacji OLE DB.  
  
## <a name="syntax"></a>Składnia

```cpp
template <  
   class T,   
   class Storage,   
   class BaseInterface = IRowsetChange,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>>  
class ATL_NO_VTABLE IRowsetChangeImpl : public BaseInterface  
```  
  
### <a name="parameters"></a>Parametry  

*T*<br/>
Klasa pochodząca z `IRowsetChangeImpl`.  
  
*Magazyn*<br/>
Rekordzie użytkownika.  
  
*BaseInterface*<br/>
Klasy dla interfejsu, takich jak bazowej `IRowsetChange`.  
  
*RowClass*<br/>
Jednostka magazynu dojście do wiersza.  
  
*MapClass*<br/>
Jednostki magazynu na potrzeby wszystkich dojść do wierszy są przechowywane przez dostawcę.  

## <a name="requirements"></a>Wymagania  

**Nagłówek:** atldb.h  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="interface-methods-used-with-irowsetchange"></a>Metody interfejsu (używana w IRowsetChange)  
  
|||  
|-|-|  
|[DeleteRows](#deleterows)|Usuwa wiersze z zestawu wierszy.|  
|[InsertRow —](#insertrow)|Wstawia wiersz do zestawu wierszy.|  
|[SetData](#setdata)|Ustawia wartości danych w co najmniej jedną kolumnę.|  
  
### <a name="implementation-method-callback"></a>Implementacja metody (wywołanie zwrotne)  
  
|||  
|-|-|  
|[FlushData](#flushdata)|Overidden przez dostawcę, aby zatwierdzić jego magazynu danych.|  
  
## <a name="remarks"></a>Uwagi  

Ten interfejs jest odpowiedzialny za operacje zapisu natychmiastowego do magazynu danych. "Natychmiastowymi" oznacza, że po użytkownik końcowy (osoby za pomocą konsumenta) sprawia, że wszelkie zmiany, te zmiany zostaną natychmiast przesłane do dane przechowywane (i nie można cofnąć).  
  
`IRowsetChangeImpl` implementuje OLE DB `IRowsetChange` interfejs, który umożliwia aktualizowanie wartości kolumn w istniejących wierszy: usuwanie wierszy, a następnie wstawianie nowych wierszy.  
  
Implementacja szablony OLE DB obsługuje podstawowych metod (`SetData`, `InsertRow`, i `DeleteRows`).  
  
> [!IMPORTANT]
>  Zdecydowanie zaleca się przeczytanie poniższej dokumentacji przed podjęciem próby wdrożenia dostawcy:  
  
- [Tworzenie aktualizowalnego dostawcy](../../data/oledb/creating-an-updatable-provider.md)  
  
- Rozdział 6 *OLE DB Podręcznik programisty*  
  
- Zobacz też sposób, w jaki `RUpdateRowset` klasa jest używana w [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) próbki.  
  
## <a name="deleterows"></a> IRowsetChangeImpl::DeleteRows

Usuwa wiersze z zestawu wierszy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
STDMETHOD (DeleteRows )(HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBROWSTATUS rgRowStatus[]);  
```  
  
#### <a name="parameters"></a>Parametry  

Zobacz [IRowsetChange::DeleteRows](/previous-versions/windows/desktop/ms724362(v%3dvs.85)) w *OLE DB Podręcznik programisty*. 

## <a name="insertrow"></a> IRowsetChangeImpl::InsertRow

Tworzy i inicjuje nowy wiersz w zestawie wierszy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
STDMETHOD (InsertRow )(HCHAPTER /* hReserved */,  
   HACCESSOR hAccessor,  
   void* pData,  
   HROW* phRow);  
```  
  
#### <a name="parameters"></a>Parametry  

Zobacz [IRowsetChange::InsertRow](/previous-versions/windows/desktop/ms716921) w *OLE DB Podręcznik programisty*. 

## <a name="setdata"></a> IRowsetChangeImpl::SetData

Ustawia wartości danych w co najmniej jedną kolumnę.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
STDMETHOD (SetData )(HROW hRow,  
   HACCESSOR hAccessor,  
   void* pSrcData);  
```  
  
#### <a name="parameters"></a>Parametry  

Zobacz [IRowsetChange::SetData](/previous-versions/windows/desktop/ms721232) w *OLE DB Podręcznik programisty*. 

## <a name="flushdata"></a> IRowsetChangeImpl::FlushData

Overidden przez dostawcę, aby zatwierdzić jego magazynu danych.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT FlushData(HROW hRowToFlush,  
   HACCESSOR hAccessorToFlush);  
```  
  
#### <a name="parameters"></a>Parametry  

*hRowToFlush*<br/>
[in] Dojście do wierszy danych. Typ ten wiersz jest określana na podstawie *RowClass* argument szablonu `IRowsetImpl` klasy (`CSimpleRow` domyślnie).  
  
*hAccessorToFlush*<br/>
[in] Dojście do metody dostępu, który zawiera informacje o powiązaniu i informacje o typie w jego `PROVIDER_MAP` (zobacz [iaccessorimpl —](../../data/oledb/iaccessorimpl-class.md)).  
  
### <a name="return-value"></a>Wartość zwracana  

Standardowa HRESULT.  
  
## <a name="see-also"></a>Zobacz też  

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)