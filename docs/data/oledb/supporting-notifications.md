---
title: Obsługa powiadomień
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [C++], OLE DB consumers
- events [C++], notifications in OLE DB
- OLE DB consumers, notifications
- rowsets, event notifications
- OLE DB provider templates, notifications
- OLE DB providers, notifications
ms.assetid: 76e875fd-2bfd-4e4e-9f43-dbe5a3fa7382
ms.openlocfilehash: d29f84a0a5b33d55c0a04a4c758050cf9746f72a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209558"
---
# <a name="supporting-notifications"></a>Obsługa powiadomień

## <a name="implementing-connection-point-interfaces-on-the-provider-and-consumer"></a>Implementowanie interfejsów punktu połączenia dla dostawcy i konsumenta

Aby zaimplementować powiadomienia, Klasa dostawcy musi dziedziczyć z [IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md) i [IConnectionPointContainer](../../atl/reference/iconnectionpointcontainerimpl-class.md).

`IRowsetNotifyCP` implementuje witrynę dostawcy dla interfejsu punktu połączenia [IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)). `IRowsetNotifyCP` implementuje funkcje emisji, aby poinformować odbiorniki w punkcie połączenia `IID_IRowsetNotify` o zmianach zawartości zestawu wierszy.

Należy również zaimplementować i zarejestrować `IRowsetNotify` na odbiorcy (znany również jako ujścia) przy użyciu [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) , aby konsument mógł obsługiwać powiadomienia. Aby uzyskać informacje na temat implementowania interfejsu punktu połączenia na odbiorcy, zobacz [otrzymywanie powiadomień](../../data/oledb/receiving-notifications.md).

Ponadto Klasa musi mieć mapę, która definiuje wpis punktu połączenia, np.:

```cpp
BEGIN_CONNECTION_POINT_MAP
   CONNECTIONPOINT_ENTRY (IID_IRowsetNotify)
END_CONNECTION_POINT_MAP
```

## <a name="adding-irowsetnotify"></a>Dodawanie IRowsetNotify

Aby dodać `IRowsetNotify`, musisz dodać `IConnectionPointContainerImpl<rowset-name>` i `IRowsetNotifyCP<rowset-name>` do łańcucha dziedziczenia.

Poniżej znajduje się na przykład łańcuch dziedziczenia dla `RUpdateRowset` w [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV):

> [!NOTE]
> Przykładowy kod może się różnić od tego, co jest wymienione tutaj; przykładowy kod należy traktować jako nowszą wersję.

```cpp
///////////////////////////////////////////////////////////////////////////
// class RUpdateRowset (in rowset.h)

class RUpdateRowset :
public CRowsetImpl< RUpdateRowset, CAgentMan, CUpdateCommand,
         CAtlArray< CAgentMan, CAtlArray<CAgentMan>>, CSimpleRow,
         IRowsetScrollImpl< RUpdateRowset, IRowsetScroll >>,
      public IRowsetUpdateImpl< RUpdateRowset, CAgentMan >,
      public IConnectionPointContainerImpl<RUpdateRowset>,
      public IRowsetNotifyCP<RUpdateRowset>
```

### <a name="setting-com-map-entries"></a>Ustawianie wpisów mapy COM

Należy również dodać następujące elementy do mapy COM w zestawie wierszy:

```cpp
COM_INTERFACE_ENTRY(IConnectionPointContainer)
COM_INTERFACE_ENTRY_IMPL(IConnectionPointContainer)
```

Makra te umożliwiają każdej osobie wywołującej `QueryInterface` dla kontenera punktu połączenia (podstawa `IRowsetNotify`) do znalezienia żądanego interfejsu dostawcy. Aby zapoznać się z przykładem użycia punktów połączenia, zobacz przykład wielokąta ATL i samouczek.

### <a name="setting-connection-point-map-entries"></a>Ustawianie wpisów mapy punktów połączenia

Należy również dodać mapę punktu połączenia. Powinien wyglądać następująco:

```cpp
BEGIN_CONNECTION_POINT_MAP(rowset-name)
     CONNECTION_POINT_ENTRY(_uuidof(IRowsetNotify))
END_CONNECTION_POINT_MAP()
```

Ta mapa punktu połączenia umożliwia składnikowi szukającemu interfejsu `IRowsetNotify` znalezienie go w dostawcy.

### <a name="setting-properties"></a>Ustawianie właściwości

Należy również dodać do dostawcy następujące właściwości. Wystarczy dodać właściwości na podstawie obsługiwanych interfejsów.

|Właściwość|Dodaj, jeśli są obsługiwane|
|--------------|------------------------|
|DBPROP_IConnectionPointContainer|Zawsze|
|DBPROP_NOTIFICATIONGRANULARITY|Zawsze|
|DBPROP_NOTIFICATIONPHASES|Zawsze|
|DBPROP_NOTIFYCOLUMNSET|`IRowsetChange`|
|DBPROP_NOTIFYROWDELETE|`IRowsetChange`|
|DBPROP_NOTIFYROWINSERT|`IRowsetChange`|
|DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE|Zawsze|
|DBPROP_NOTIFYROWFIRSTCHANGE|`IRowsetUpdate`|
|DBPROP_NOTIFYROWSETRELEASE|Zawsze|
|DBPROP_NOTIFYROWUNDOCHANGE|`IRowsetUpdate`|
|DBPROP_NOTIFYROWUNDODELETE|`IRowsetUpdate`|
|DBPROP_NOTIFYROWUNDOINSERT|`IRowsetUpdate`|
|DBPROP_NOTIFYROWUPDATE|`IRowsetUpdate`|

Większość implementacji powiadomień jest już osadzonych w szablonach dostawcy OLE DB. Jeśli nie dodasz `IRowsetNotifyCP` do łańcucha dziedziczenia, kompilator usunie cały kod ze strumienia kompilacji, co sprawia, że rozmiar kodu jest mniejszy.

## <a name="see-also"></a>Zobacz też

[Zaawansowane techniki dostawcy](../../data/oledb/advanced-provider-techniques.md)
