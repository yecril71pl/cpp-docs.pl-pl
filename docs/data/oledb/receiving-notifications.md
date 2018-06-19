---
title: Odbieranie powiadomień | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- notifications [C++], OLE DB consumers
- receiving notifications in OLE DB
- events [C++], notifications in OLE DB
- notifications [C++], events
- OLE DB consumers, notifications
- rowsets, event notifications
- OLE DB providers, notifications
ms.assetid: 305a1103-0c87-40c8-94bc-7fbbdd52ae32
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d9e1dee5c63281c729cdb798a190938c6433aac0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33112319"
---
# <a name="receiving-notifications"></a>Odbieranie powiadomień
OLE DB zawiera interfejsy odbieranie powiadomień w przypadku wystąpienia zdarzeń. Te ustawienia zostały opisane w [OLE DB obiektu powiadomienia](https://msdn.microsoft.com/en-us/library/ms725406.aspx) w *OLE DB Podręcznik programisty*. Ustawienia te zdarzenia używa standardowe mechanizmu COM w punktu połączenia. Na przykład obiekt ATL, który chce pobierać za pośrednictwem zdarzenia `IRowsetNotify` implementuje `IRowsetNotify` interfejsu przez dodanie `IRowsetNotify` do listy Klasa pochodna i ujawnienie go za pośrednictwem **com_interface_entry —** makra.  
  
 `IRowsetNotify` ma trzy metody, które można wywołać w różnym czasie. Jeśli chcesz odpowiedzieć tylko jeden z tych metod, możesz użyć [irowsetnotifyimpl —](../../data/oledb/irowsetnotifyimpl-class.md) klasy, która zwraca **E_NOTIMPL** dla metod nie są zainteresowane.  
  
 Podczas tworzenia zestawu wierszy, należy wskazać dostawcy czy chcesz, aby zestaw wierszy zwrócony obiekt do obsługi **IConnectionPointContainer**, który jest wymagany, aby skonfigurować powiadomienia.  
  
 Poniższy kod przedstawia sposób Otwórz zestaw wierszy z obiektu ATL i użyj `AtlAdvise` funkcji, aby skonfigurować odbioru powiadomienia. `AtlAdvise` Zwraca wartość pliku cookie, który jest używany podczas wywoływania `AtlUnadvise`.  
  
```  
CDBPropSet propset(DBPROPSET_ROWSET);  

propset.AddProperty(DBPROP_IConnectionPointContainer, true);  
  

product.Open(session, _T("Products"), &propset);  
  

AtlAdvise(product.m_spRowset, GetUnknown(), IID_IRowsetNotify, &m_dwCookie);  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)