---
title: Irowsetnotifycp — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetNotifyCP
- Fire_OnFieldChange
- ATL::IRowsetNotifyCP::Fire_OnFieldChange
- ATL.IRowsetNotifyCP.Fire_OnFieldChange
- IRowsetNotifyCP.Fire_OnFieldChange
- IRowsetNotifyCP::Fire_OnFieldChange
- IRowsetNotifyCP.Fire_OnRowChange
- ATL.IRowsetNotifyCP.Fire_OnRowChange
- Fire_OnRowChange
- ATL::IRowsetNotifyCP::Fire_OnRowChange
- IRowsetNotifyCP::Fire_OnRowChange
- Fire_OnRowsetChange
- IRowsetNotifyCP::Fire_OnRowsetChange
- IRowsetNotifyCP.Fire_OnRowsetChange
- ATL::IRowsetNotifyCP::Fire_OnRowsetChange
- ATL.IRowsetNotifyCP.Fire_OnRowsetChange
dev_langs:
- C++
helpviewer_keywords:
- IRowsetNotifyCP class
- Fire_OnFieldChange method
- Fire_OnRowChange method
- Fire_OnRowsetChange method
ms.assetid: ccef402b-94a0-4c2e-9a13-7e854ef82390
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cf7cde624eeaa8a65ba5d5a2b4729ee94847d0e9
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2018
ms.locfileid: "39338184"
---
# <a name="irowsetnotifycp-class"></a>IRowsetNotifyCP — Klasa
Implementuje witryny dostawcy interfejsu punktu połączenia [IRowsetNotify](https://msdn.microsoft.com/library/ms712959.aspx).  
  
## <a name="syntax"></a>Składnia

```cpp
template <class T, class ReentrantEventSync = CComSharedMutex>  
class IRowsetNotifyCP :   
   public IConnectionPointImpl<  
      T,   
      piid = &__uuidof(IRowsetNotify),   
      CComDynamicUnkArray DynamicUnkArray>,  
   public ReentrantEventSync  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Klasa pochodząca z `IRowsetNotifyCP`.  
  
 *ReentrantEventSync*  
 Mutex — klasa, która obsługuje współużytkowania wątkowości (wartość domyślna to `CComSharedMutex`). Mutex jest obiektem synchronizacji, która umożliwia jeden wątek wzajemnie wykluczających się uzyskanie dostępu do zasobu.  
  
 *piid*  
 Wskaźnik identyfikator interfejsu (`IID*`) dla `IRowsetNotify` interfejsu punktu połączenia. Wartość domyślna to `&__uuidof(IRowsetNotify)`.  
  
 *DynamicUnkArray*  
 Tablica typu [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), który jest dynamicznie przydzielanej tablicy `IUnknown` wskaźników do klienta ujścia interfejsów. 

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h   
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Fire_OnFieldChange](#onfieldchange)|Powiadamia klientów zmiany wartości kolumny.|  
|[Fire_OnRowChange](#onrowchange)|Powiadamia klientów zmiany wpływające na wiersze.|  
|[Fire_OnRowsetChange](#onrowsetchange)|Powiadamia klientów zmiany wpływające na cały zestaw wierszy.|  
  
## <a name="remarks"></a>Uwagi  
 `IRowsetNotifyCP` implementuje funkcje, które można wykonać funkcji advise odbiorników dla punktu połączenia można rozgłaszać `IID_IRowsetNotify` zmian zawartości zestawu wierszy.  
  
 Należy zauważyć, że należy również wdrożyć i zarejestrować `IRowsetNotify` na odbiorcę (znany także jako "obiekt sink"), za pomocą [irowsetnotifyimpl —](../../data/oledb/irowsetnotifyimpl-class.md) , dzięki czemu użytkownik może obsługiwać powiadomienia. Zobacz [odbieranie powiadomień](../../data/oledb/receiving-notifications.md) dotyczących implementowania interfejsu punktu połączenia na odbiorcy.  
  
 Szczegółowe informacje na temat implementowania powiadomień, zobacz "Obsługi powiadomienia" w [tworzenie aktualizowalnego dostawcy](../../data/oledb/creating-an-updatable-provider.md).  

## <a name="onfieldchange"></a> IRowsetNotifyCP::Fire_OnFieldChange
Emituje [onfieldchange —](https://msdn.microsoft.com/library/ms715961.aspx) zdarzenia w celu powiadamiania odbiorców o zmianie wartości kolumny.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Fire_OnFieldChange(IRowset* pRowset,  
   HROW hRow,  
   DBORDINAL cColumns,  
   DBORDINAL* rgColumns,  
   DBREASON eReason,  
   DBEVENTPHASE ePhase,  
   BOOL fCantDeny);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IRowsetNotify::OnFieldChange](https://msdn.microsoft.com/library/ms715961.aspx) w *OLE DB Podręcznik programisty*. 

## <a name="onrowchange"></a> IRowsetNotifyCP::Fire_OnRowChange
Emituje [onrowchange —](https://msdn.microsoft.com/library/ms722694.aspx) zdarzenie do wszystkich obiektów nasłuchujących dla punktu połączenia `IID_IRowsetNotify` do powiadamiania klientów zmiany wpływające na wiersze.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Fire_OnRowChange(IRowset* pRowset,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBREASON eReason,  
   DBEVENTPHASE ePhase,  
   BOOL fCantDeny);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IRowsetNotify::OnRowChange](https://msdn.microsoft.com/library/ms722694.aspx) w *OLE DB Podręcznik programisty*.  

## <a name="onrowsetchange"></a> IRowsetNotifyCP::Fire_OnRowsetChange
Emituje [onrowsetchange —](https://msdn.microsoft.com/library/ms722669.aspx) zdarzenie do wszystkich obiektów nasłuchujących dla punktu połączenia `IID_IRowsetNotify` do powiadamiania klientów zmiany wpływające na cały zestaw wierszy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Fire_OnRowsetChange(IRowset* pRowset,  
   DBREASON eReason,  
   DBEVENTPHASE ePhase,  
   BOOL fCantDeny);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/library/ms722669.aspx) w *OLE DB Podręcznik programisty*.
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Powiadomienia (COM)](http://msdn.microsoft.com/library/windows/desktop/ms678433)   
 [BEGIN_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#begin_connection_point_map)   
 [END_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#end_connection_point_map)   
 [CONNECTION_POINT_ENTRY](../../atl/reference/connection-point-macros.md#connection_point_entry)   
 [Tworzenie aktualizowalnego dostawcy](../../data/oledb/creating-an-updatable-provider.md)