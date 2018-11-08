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
ms.openlocfilehash: 2e5327f2197a1d48542ad5f7a615294a915948f5
ms.sourcegitcommit: 943c792fdabf01c98c31465f23949a829eab9aad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2018
ms.locfileid: "51265025"
---
# <a name="supporting-notifications"></a>Obsługa powiadomień

## <a name="implementing-connection-point-interfaces-on-the-provider-and-consumer"></a>Implementacja interfejsów punktu połączenia dostawcy i klienta

Aby zaimplementować powiadomienia, klasa dostawcy musi dziedziczyć z [irowsetnotifycp —](../../data/oledb/irowsetnotifycp-class.md) i [interfejsy IConnectionPointContainer](../../atl/reference/iconnectionpointcontainerimpl-class.md).

`IRowsetNotifyCP` implementuje witryny dostawcy interfejsu punktu połączenia [IRowsetNotify](/previous-versions/windows/desktop/ms712959). `IRowsetNotifyCP` implementuje funkcje, które można wykonać funkcji advise odbiorników dla punktu połączenia można rozgłaszać `IID_IRowsetNotify` zmian zawartości zestawu wierszy.

Należy również wdrożyć i zarejestrować `IRowsetNotify` na odbiorcę (znany także jako ujścia) za pomocą [irowsetnotifyimpl —](../../data/oledb/irowsetnotifyimpl-class.md) , dzięki czemu użytkownik może obsługiwać powiadomienia. Aby uzyskać informacji na temat implementowania interfejsu punktu połączenia na użytkownika, zobacz [odbieranie powiadomień](../../data/oledb/receiving-notifications.md).

Ponadto klasa musi mieć mapę, która definiuje wpis punktu połączenia następująco:

```cpp
BEGIN_CONNECTION_POINT_MAP
   CONNECTIONPOINT_ENTRY (IID_IRowsetNotify)
END_CONNECTION_POINT_MAP
```

## <a name="adding-irowsetnotify"></a>Dodawanie IRowsetNotify

Aby dodać `IRowsetNotify`, należy dodać `IConnectionPointContainerImpl<rowset-name>` i `IRowsetNotifyCP<rowset-name>` na swój łańcuch dziedziczenia.

Na przykład, w tym miejscu jest łańcuch dziedziczenia dla `RUpdateRowset` w [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV):

> [!NOTE]
> Przykładowy kod różnić się od wymienione tutaj; w przykładowym kodzie powinno być traktowane jako bardziej aktualnej wersji.

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

### <a name="setting-com-map-entries"></a>Ustawienie wpisy mapy interfejsu COM

Trzeba będzie również od tego, Dodaj następujący element do mapy COM w swojej wierszy:

```cpp
COM_INTERFACE_ENTRY(IConnectionPointContainer)
COM_INTERFACE_ENTRY_IMPL(IConnectionPointContainer)
```

Te makra zezwala wszystkim wywoływania `QueryInterface` kontenera punktu połączenia (podstawa `IRowsetNotify`) można znaleźć żądanego interfejsu w dostawcy usługi. Na przykład jak używać punktów połączenia, zobacz przykład WIELOKĄTA ATL i samouczków.

### <a name="setting-connection-point-map-entries"></a>Ustawienie wpisy mapy punktu połączenia

Należy również dodać mapę punktu połączenia. Powinien wyglądać mniej więcej tak:

```cpp
BEGIN_CONNECTION_POINT_MAP(rowset-name)
     CONNECTION_POINT_ENTRY(_uuidof(IRowsetNotify))
END_CONNECTION_POINT_MAP()
```

Ta mapa punktu połączenia umożliwia składnik Wyszukiwanie `IRowsetNotify` interfejsu, aby je znaleźć w dostawcy.

### <a name="setting-properties"></a>Ustawianie właściwości

Musisz również dodać następujące właściwości dostawcy. Wystarczy dodać właściwości oparte na interfejsach, które obsługujesz.

|Właściwość|Dodawanie, jeśli obsługuje|
|--------------|------------------------|
|DBPROP_IConnectionPointContainer|zawsze|
|DBPROP_NOTIFICATIONGRANULARITY|zawsze|
|DBPROP_NOTIFICATIONPHASES|zawsze|
|DBPROP_NOTIFYCOLUMNSET|`IRowsetChange`|
|DBPROP_NOTIFYROWDELETE|`IRowsetChange`|
|DBPROP_NOTIFYROWINSERT|`IRowsetChange`|
|DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE|zawsze|
|DBPROP_NOTIFYROWFIRSTCHANGE|`IRowsetUpdate`|
|DBPROP_NOTIFYROWSETRELEASE|zawsze|
|DBPROP_NOTIFYROWUNDOCHANGE|`IRowsetUpdate`|
|DBPROP_NOTIFYROWUNDODELETE|`IRowsetUpdate`|
|DBPROP_NOTIFYROWUNDOINSERT|`IRowsetUpdate`|
|DBPROP_NOTIFYROWUPDATE|`IRowsetUpdate`|

Większość implementacji powiadomienia już jest osadzony w szablony OLE DB Provider. Jeśli nie dodasz `IRowsetNotifyCP` na swój łańcuch dziedziczenia kompilator usuwa ten kod z strumienia kompilacji, dzięki czemu mniejszy rozmiar kodu.

## <a name="see-also"></a>Zobacz też

[Zaawansowane techniki dostawcy](../../data/oledb/advanced-provider-techniques.md)