---
title: Obsługa powiadomień | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- notifications [C++], OLE DB consumers
- events [C++], notifications in OLE DB
- OLE DB consumers, notifications
- rowsets, event notifications
- OLE DB provider templates, notifications
- OLE DB providers, notifications
ms.assetid: 76e875fd-2bfd-4e4e-9f43-dbe5a3fa7382
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f750346b0fdd8821800b012b3cdff7acc12f7897
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="supporting-notifications"></a>Obsługa powiadomień
## <a name="implementing-connection-point-interfaces-on-the-provider-and-consumer"></a>Implementowanie interfejsów punktu połączenia w dostawcy i klienta  
 Aby zaimplementować powiadomienia, klasa dostawcy musi dziedziczyć z [irowsetnotifycp —](../../data/oledb/irowsetnotifycp-class.md) i [IConnectionPointContainer](../../atl/reference/iconnectionpointcontainerimpl-class.md).  
  
 `IRowsetNotifyCP` implementuje witryna dostawcy dla interfejsu punktu połączenia [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx). `IRowsetNotifyCP` implementuje emisji funkcji w celu poinformowania odbiorników w punkcie połączenia **IID_IRowsetNotify** zmian zawartości zestawu wierszy.  
  
 Należy pamiętać, że musi również wdrożyć i zarejestrować `IRowsetNotify` na konsumenta (znanej także jako obiekt sink) przy użyciu [irowsetnotifyimpl —](../../data/oledb/irowsetnotifyimpl-class.md) , dzięki czemu klient może obsłużyć powiadomienia. Informacje o implementacji interfejsu punktu połączenia dla konsumenta, zobacz [odbieranie powiadomień](../../data/oledb/receiving-notifications.md).  
  
 Ponadto klasa musi zawierać również mapy definiuje wpis punktu połączenia, jak to:  
  
```  
BEGIN_CONNECTION_POINT_MAP  
   CONNECTIONPOINT_ENTRY (IID_IRowsetNotify)  
END_CONNECTION_POINT_MAP  
```  
  
## <a name="adding-irowsetnotify"></a>Dodawanie IRowsetNotify  
 Aby dodać `IRowsetNotify`, należy dodać `IConnectionPointContainerImpl<rowset-name>` i `IRowsetNotifyCP<rowset-name>` Twojego łańcucha dziedziczenia.  
  
 Na przykład, w tym miejscu jest łańcuch dziedziczenia dla `RUpdateRowset` w [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f):  
  
> [!NOTE]
>  Przykładowy kod mogą być inne niż wymienione w tym miejscu; Przykładowy kod powinno być traktowane jako bardziej zaktualizowanej wersji.  
  
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
  
### <a name="setting-com-map-entries"></a>Ustawienie wpisów COM Map  
 Należy również dodać następujące na mapie modelu COM w Twojej wierszy:  
  
```  
COM_INTERFACE_ENTRY(IConnectionPointContainer)  
COM_INTERFACE_ENTRY_IMPL(IConnectionPointContainer)  
```  
  
 Te makra zezwala wszystkim wywoływania `QueryInterface` z kontenera punktu połączenia (podstawę `IRowsetNotify`) można znaleźć żądanego interfejsu w dostawcy. Na przykład sposobu użycia punkty połączenia Zobacz przykład WIELOKĄTA ATL i samouczka.  
  
### <a name="setting-connection-point-map-entries"></a>Ustawienie wpisów Map punktu połączenia  
 Należy również dodać mapy punktu połączenia. Powinien wyglądać mniej więcej tak:  
  
```  
BEGIN_CONNECTION_POINT_MAP(rowset-name)  
     CONNECTION_POINT_ENTRY(_uuidof(IRowsetNotify))  
END_CONNECTION_POINT_MAP()  
```  
  
 Ta mapa punktu połączenia umożliwia wyszukiwanie składnika `IRowsetNotify` interfejsu znajdź go w dostawcy.  
  
### <a name="setting-properties"></a>Ustawianie właściwości  
 Należy również dodać następujące właściwości dostawcy. Należy dodać właściwości, w oparciu o interfejsy obsługiwane.  
  
|Właściwość|Dodawanie, jeśli obsługuje|  
|--------------|------------------------|  
|**DBPROP_IConnectionPointContainer**|Zawsze|  
|**DBPROP_NOTIFICATIONGRANULARITY**|Zawsze|  
|**DBPROP_NOTIFICATIONPHASES**|Zawsze|  
|**DBPROP_NOTIFYCOLUMNSET**|`IRowsetChange`|  
|**DBPROP_NOTIFYROWDELETE**|`IRowsetChange`|  
|**DBPROP_NOTIFYROWINSERT**|`IRowsetChange`|  
|**DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE**|Zawsze|  
|**DBPROP_NOTIFYROWFIRSTCHANGE**|`IRowsetUpdate`|  
|**DBPROP_NOTIFYROWSETRELEASE**|Zawsze|  
|**DBPROP_NOTIFYROWUNDOCHANGE**|`IRowsetUpdate`|  
|**DBPROP_NOTIFYROWUNDODELETE**|`IRowsetUpdate`|  
|**DBPROP_NOTIFYROWUNDOINSERT**|`IRowsetUpdate`|  
|**DBPROP_NOTIFYROWUPDATE**|`IRowsetUpdate`|  
  
 Większość implementację dla powiadomień już jest osadzony w szablony OLE DB Provider. Jeśli nie dodasz `IRowsetNotifyCP` Twojego łańcucha dziedziczenia kompilator usuwa ten kod strumienia kompilacji, dzięki czemu mniejszy rozmiar kodu.  
  
## <a name="see-also"></a>Zobacz też  
 [Zaawansowane techniki dostawcy](../../data/oledb/advanced-provider-techniques.md)