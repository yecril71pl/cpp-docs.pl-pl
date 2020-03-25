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
ms.openlocfilehash: fa85bc7947b3b446ec7c6d3fdb0d7b62d308fb53
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210330"
---
# <a name="irowsetnotifycp-class"></a>IRowsetNotifyCP — Klasa

Implementuje witrynę dostawcy dla interfejsu punktu połączenia [IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)).

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

*&*<br/>
Klasa pochodna `IRowsetNotifyCP`.

*ReentrantEventSync*<br/>
Klasa mutex, która obsługuje współużytkowania wątkowości (wartość domyślna to `CComSharedMutex`). Mutex jest obiektem synchronizacji, który umożliwia jednemu wątkowi wyłączny dostęp do zasobu.

*piid*<br/>
Wskaźnik identyfikatora interfejsu (`IID*`) dla interfejsu punktu połączenia `IRowsetNotify`. Wartością domyślną jest `&__uuidof(IRowsetNotify)`.

*DynamicUnkArray*<br/>
Tablica typu [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), która jest dynamicznie przydzieloną tablicą `IUnknown` wskaźników do interfejsów ujścia klienta.

## <a name="requirements"></a>Wymagania

**Nagłówek:** ATLDB. h

## <a name="members"></a>Members

### <a name="methods"></a>Metody

|||
|-|-|
|[Fire_OnFieldChange](#onfieldchange)|Powiadamia konsumenta o zmianie wartości w kolumnie.|
|[Fire_OnRowChange](#onrowchange)|Powiadamia konsumenta o zmianie wpływającej na wiersze.|
|[Fire_OnRowsetChange](#onrowsetchange)|Powiadamia konsumenta o zmianie wpływającej na cały zestaw wierszy.|

## <a name="remarks"></a>Uwagi

`IRowsetNotifyCP` implementuje funkcje emisji, aby poinformować odbiorniki w punkcie połączenia `IID_IRowsetNotify` o zmianach zawartości zestawu wierszy.

Należy pamiętać, że należy również zaimplementować i zarejestrować `IRowsetNotify` na odbiorcy (znany również jako "ujścia") za pomocą [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) , aby konsument mógł obsługiwać powiadomienia. Zobacz [otrzymywanie powiadomień](../../data/oledb/receiving-notifications.md) dotyczących implementowania interfejsu punktu połączenia na odbiorcy.

Aby uzyskać szczegółowe informacje na temat implementowania powiadomień, zobacz "Obsługa powiadomień" w temacie [Tworzenie aktualizowalnego dostawcy](../../data/oledb/creating-an-updatable-provider.md).

## <a name="irowsetnotifycpfire_onfieldchange"></a><a name="onfieldchange"></a>IRowsetNotifyCP:: Fire_OnFieldChange

Emituje zdarzenie [OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) , aby poinformować odbiorców o zmianie wartości kolumny.

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

Zobacz [IRowsetNotify:: OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="irowsetnotifycpfire_onrowchange"></a><a name="onrowchange"></a>IRowsetNotifyCP:: Fire_OnRowChange

Emituje zdarzenie [OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) do wszystkich odbiorników w punkcie połączenia `IID_IRowsetNotify`, aby poinformować odbiorców o zmianie wpływającej na wiersze.

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

Zobacz [IRowsetNotify:: OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="irowsetnotifycpfire_onrowsetchange"></a><a name="onrowsetchange"></a>IRowsetNotifyCP:: Fire_OnRowsetChange

Emituje zdarzenie [OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) do wszystkich odbiorników w punkcie połączenia `IID_IRowsetNotify`, aby poinformować odbiorców o zmianie wpływającej na cały zestaw wierszy.

### <a name="syntax"></a>Składnia

```cpp
HRESULT Fire_OnRowsetChange(IRowset* pRowset,
   DBREASON eReason,
   DBEVENTPHASE ePhase,
   BOOL fCantDeny);
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowsetNotify:: OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[Powiadomienia (COM)](/windows/win32/com/notifications)<br/>
[BEGIN_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#begin_connection_point_map)<br/>
[END_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#end_connection_point_map)<br/>
[CONNECTION_POINT_ENTRY](../../atl/reference/connection-point-macros.md#connection_point_entry)<br/>
[Tworzenie aktualizowalnego dostawcy](../../data/oledb/creating-an-updatable-provider.md)
