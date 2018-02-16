---
title: "Odbieranie powiadomień | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 29e82458f56c9b1f321f7a82afeb6f041be27854
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
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