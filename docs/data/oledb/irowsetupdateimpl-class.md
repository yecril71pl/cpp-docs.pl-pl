---
title: Irowsetupdateimpl — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetUpdateImpl
- ATL.IRowsetUpdateImpl
- ATL::IRowsetUpdateImpl
dev_langs:
- C++
helpviewer_keywords:
- providers, updatable
- IRowsetUpdateImpl class
- updatable providers, deferred update
ms.assetid: f85af76b-ab6f-4f8b-8f4a-337c9679d68f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 34efd252f67a0e3da9827ef97cff8bcab0a45532
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="irowsetupdateimpl-class"></a>IRowsetUpdateImpl — Klasa
Szablony OLE DB stosowania [IRowsetUpdate](https://msdn.microsoft.com/en-us/library/ms714401.aspx) interfejsu.  
  
## <a name="syntax"></a>Składnia

```cpp
template <  
   class T,   
   class Storage,   
   class UpdateArray = CAtlArray<Storage>,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>   
>  

class IRowsetUpdateImpl : public IRowsetChangeImpl<  
   T,   
   Storage,   
   IRowsetUpdate,   
   RowClass,   
   MapClass>  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Klasa pochodna od `IRowsetUpdateImpl`.  
  
 `Storage`  
 Rekord użytkownika.  
  
 `UpdateArray`  
 Tablica zawierająca dane z pamięci podręcznej do aktualizacji zestawu wierszy.  
  
 `RowClass`  
 Jednostki magazynu dla **HROW**.  
  
 `MapClass`  
 Jednostki magazynu dla wszystkich dojść do wierszy posiadanych przez dostawcę.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="interface-methods-used-with-irowsetchange"></a>Metody interfejsu (używane z IRowsetChange)  
  
|||  
|-|-|  
|[SetData](../../data/oledb/irowsetupdateimpl-setdata.md)|Ustawia wartości danych w co najmniej jedną kolumnę.|  
  
### <a name="interface-methods-used-with-irowsetupdate"></a>Metody interfejsu (używane z IRowsetUpdate)  
  
|||  
|-|-|  
|[GetOriginalData](../../data/oledb/irowsetupdateimpl-getoriginaldata.md)|Pobiera dane ostatnio przekazywane lub uzyskiwane ze źródła danych, ignorowanie oczekujące zmiany.|  
|[GetPendingRows](../../data/oledb/irowsetupdateimpl-getpendingrows.md)|Zwraca listę wierszy z oczekującymi zmianami.|  
|[GetRowStatus](../../data/oledb/irowsetupdateimpl-getrowstatus.md)|Zwraca informacje o stanie określonych wierszy.|  
|[Cofnij](../../data/oledb/irowsetupdateimpl-undo.md)|Umożliwia cofnięcie zmian do wiersza od czasu ostatniego pobrania lub aktualizacji.|  
|[Aktualizacja](../../data/oledb/irowsetupdateimpl-update.md)|Przesyła zmiany wprowadzone od czasu ostatniego pobrania lub aktualizacji wiersza.|  
  
### <a name="implementation-methods-callback"></a>Implementacja metody (wywołanie zwrotne)  
  
|||  
|-|-|  
|[IsUpdateAllowed](../../data/oledb/irowsetupdateimpl-isupdateallowed.md)|Używany do sprawdzania zabezpieczeń, integralność i tak dalej przed zezwoleniem na aktualizacje.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|||  
|-|-|  
|[m_mapCachedData](../../data/oledb/irowsetupdateimpl-m-mapcacheddata.md)|Zawiera oryginalnych danych dla operacji opóźnieniem.|  
  
## <a name="remarks"></a>Uwagi  
 Należy najpierw przeczytać i zrozumieć dokumentację [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx), ponieważ wszystkie elementy opisane ma również zastosowanie w tym miejscu. Należy przeczytać Rozdział 6 *OLE DB Podręcznik programisty* na temat ustawiania danych.  
  
 `IRowsetUpdateImpl` implementuje OLE DB `IRowsetUpdate` interfejs, który umożliwia opóźnienia przekazania zmiany wprowadzone w `IRowsetChange` do źródła danych, a Cofnij zmiany przed ich przesłaniem.  
  
> [!IMPORTANT]
>  Zdecydowanie zaleca się przeczytanie następujących dokumentacji, przed przystąpieniem do implementowania dostawcy:  
  
-   [Tworzenie aktualizowalnego dostawcy](../../data/oledb/creating-an-updatable-provider.md)  
  
-   Rozdział 6 *OLE DB Podręcznik programisty*  
  
-   Zobacz też sposób `RUpdateRowset` klasa jest używana w przykładowym UpdatePV  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Tworzenie aktualizowalnego dostawcy](../../data/oledb/creating-an-updatable-provider.md)