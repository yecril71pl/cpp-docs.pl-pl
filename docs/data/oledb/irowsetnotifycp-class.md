---
title: IRowsetNotifyCP — Klasa
ms.date: 11/04/2016
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
helpviewer_keywords:
- IRowsetNotifyCP class
- Fire_OnFieldChange method
- Fire_OnRowChange method
- Fire_OnRowsetChange method
ms.assetid: ccef402b-94a0-4c2e-9a13-7e854ef82390
ms.openlocfilehash: 119cc79cf0f3ed5784e1b3b291fce52f06695d36
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556286"
---
# <a name="irowsetnotifycp-class"></a>IRowsetNotifyCP — Klasa

Implementuje witryny dostawcy interfejsu punktu połączenia [IRowsetNotify](https://docs.microsoft.com/previous-versions/windows/desktop/ms712959(v=vs.85)).

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

*T*<br/>
Klasa pochodząca z `IRowsetNotifyCP`.

*ReentrantEventSync*<br/>
Mutex — klasa, która obsługuje współużytkowania wątkowości (wartość domyślna to `CComSharedMutex`). Mutex jest obiektem synchronizacji, która umożliwia jeden wątek wzajemnie wykluczających się uzyskanie dostępu do zasobu.

*piid*<br/>
Wskaźnik identyfikator interfejsu (`IID*`) dla `IRowsetNotify` interfejsu punktu połączenia. Wartość domyślna to `&__uuidof(IRowsetNotify)`.

*DynamicUnkArray*<br/>
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

Emituje [onfieldchange —](https://docs.microsoft.com/previous-versions/windows/desktop/ms715961(v=vs.85)) zdarzenia w celu powiadamiania odbiorców o zmianie wartości kolumny.

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

Zobacz [IRowsetNotify::OnFieldChange](https://docs.microsoft.com/previous-versions/windows/desktop/ms715961(v=vs.85)) w *OLE DB Podręcznik programisty*.

## <a name="onrowchange"></a> IRowsetNotifyCP::Fire_OnRowChange

Emituje [onrowchange —](https://docs.microsoft.com/previous-versions/windows/desktop/ms722694(v=vs.85)) zdarzenie do wszystkich obiektów nasłuchujących dla punktu połączenia `IID_IRowsetNotify` do powiadamiania klientów zmiany wpływające na wiersze.

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

Zobacz [IRowsetNotify::OnRowChange](https://docs.microsoft.com/previous-versions/windows/desktop/ms722694(v=vs.85)) w *OLE DB Podręcznik programisty*.

## <a name="onrowsetchange"></a> IRowsetNotifyCP::Fire_OnRowsetChange

Emituje [onrowsetchange —](https://docs.microsoft.com/previous-versions/windows/desktop/ms722669(v=vs.85)) zdarzenie do wszystkich obiektów nasłuchujących dla punktu połączenia `IID_IRowsetNotify` do powiadamiania klientów zmiany wpływające na cały zestaw wierszy.

### <a name="syntax"></a>Składnia

```cpp
HRESULT Fire_OnRowsetChange(IRowset* pRowset,
   DBREASON eReason,
   DBEVENTPHASE ePhase,
   BOOL fCantDeny);
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowsetNotify::OnRowsetChange](https://docs.microsoft.com/previous-versions/windows/desktop/ms722669(v=vs.85)) w *OLE DB Podręcznik programisty*.

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[Powiadomienia (COM)](/windows/desktop/com/notifications)<br/>
[BEGIN_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#begin_connection_point_map)<br/>
[END_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#end_connection_point_map)<br/>
[CONNECTION_POINT_ENTRY](../../atl/reference/connection-point-macros.md#connection_point_entry)<br/>
[Tworzenie aktualizowalnego dostawcy](../../data/oledb/creating-an-updatable-provider.md)