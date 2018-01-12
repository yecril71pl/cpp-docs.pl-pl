---
title: "Irowsetnotifycp — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IRowsetNotifyCP
dev_langs: C++
helpviewer_keywords: IRowsetNotifyCP class
ms.assetid: ccef402b-94a0-4c2e-9a13-7e854ef82390
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bae872c90a6df76e3efc1fce1aab6e77bc8fd313
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="irowsetnotifycp-class"></a>IRowsetNotifyCP — Klasa
Implementuje witryna dostawcy dla interfejsu punktu połączenia [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
template <  
   class T,   
   class ReentrantEventSync = CComSharedMutex   
>  
class IRowsetNotifyCP :   
   public IConnectionPointImpl<  
      T,   
      piid = &__uuidof(IRowsetNotify),   
      CComDynamicUnkArray DynamicUnkArray  
   >,  
   public ReentrantEventSync  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Klasa pochodna od `IRowsetNotifyCP`.  
  
 `ReentrantEventSync`  
 Mutex — klasa, która obsługuje ponowne wejście (wartość domyślna to **CComSharedMutex**). Obiektu mutex jest obiekt synchronizacji, umożliwiająca jeden wątek wykluczają się wzajemnie dostęp do zasobu.  
  
 `piid`  
 Wskaźnik Identyfikatora interfejsu (**IID\***) dla **IRowsetNotify** interfejsu punktu połączenia. Wartość domyślna to **& __uuidof(IRowsetNotify)**.  
  
 `DynamicUnkArray`  
 Tablica typu [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), czyli dynamicznie przydzielonego tablicę **IUnknown** interfejsy sink wskaźników do klienta.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Fire_OnFieldChange](../../data/oledb/irowsetnotifycp-fire-onfieldchange.md)|Powiadamia konsumenta zmianę wartości kolumny.|  
|[Fire_OnRowChange](../../data/oledb/irowsetnotifycp-fire-onrowchange.md)|Powiadamia użytkownika zmian wpływających na wiersze.|  
|[Fire_OnRowsetChange](../../data/oledb/irowsetnotifycp-fire-onrowsetchange.md)|Powiadamia konsumenta zmian wpływających na cały zestaw wierszy.|  
  
## <a name="remarks"></a>Uwagi  
 `IRowsetNotifyCP`implementuje emisji funkcji w celu poinformowania odbiorników w punkcie połączenia **IID_IRowsetNotify** zmian zawartości zestawu wierszy.  
  
 Należy pamiętać, że musi również wdrożyć i zarejestrować `IRowsetNotify` na konsumenta (znanej także jako "sink"), za pomocą [irowsetnotifyimpl —](../../data/oledb/irowsetnotifyimpl-class.md) , dzięki czemu klient może obsłużyć powiadomienia. Zobacz [odbieranie powiadomień](../../data/oledb/receiving-notifications.md) o implementacji interfejsu punktu połączenia dla konsumenta.  
  
 Aby uzyskać szczegółowe informacje dotyczące implementacji powiadomień, zobacz "Obsługa powiadomienia" w [tworzenie aktualizowalnego dostawcy](../../data/oledb/creating-an-updatable-provider.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Powiadomienia (COM)](http://msdn.microsoft.com/library/windows/desktop/ms678433)   
 [BEGIN_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#begin_connection_point_map)   
 [END_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#end_connection_point_map)   
 [CONNECTION_POINT_ENTRY](../../atl/reference/connection-point-macros.md#connection_point_entry)   
 [Tworzenie aktualizowalnego dostawcy](../../data/oledb/creating-an-updatable-provider.md)