---
title: Odbieranie powiadomień
ms.date: 10/24/2018
helpviewer_keywords:
- notifications [C++], OLE DB consumers
- receiving notifications in OLE DB
- events [C++], notifications in OLE DB
- notifications [C++], events
- OLE DB consumers, notifications
- rowsets, event notifications
- OLE DB providers, notifications
ms.assetid: 305a1103-0c87-40c8-94bc-7fbbdd52ae32
ms.openlocfilehash: 4b630a9728770a5e35e6d6300cf465b90238350c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209803"
---
# <a name="receiving-notifications"></a>Odbieranie powiadomień

OLE DB udostępnia interfejsy do otrzymywania powiadomień w przypadku wystąpienia zdarzeń. Są one opisane w [OLE DB powiadomienia dotyczące obiektów](/previous-versions/windows/desktop/ms725406(v=vs.85)) w **odniesieniu do OLE DB programisty**. Konfiguracja tych zdarzeń używa standardowego mechanizmu punktu połączenia modelu COM. Na przykład obiekt ATL, który chce pobrać zdarzenia za pomocą `IRowsetNotify` implementuje interfejs `IRowsetNotify` przez dodanie `IRowsetNotify` do listy pochodnej klasy i udostępnienie go za pomocą makra COM_INTERFACE_ENTRY.

`IRowsetNotify` ma trzy metody, które można wywoływać w różnym czasie. Jeśli chcesz odpowiedzieć tylko na jedną z tych metod, możesz użyć klasy [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) , która zwraca E_NOTIMPL dla nieinteresujących Cię metod.

Podczas tworzenia zestawu wierszy należy poinformować dostawcę, że ma on obsługiwać zwracany obiekt zestawu wierszy `IConnectionPointContainer`, co jest potrzebne do skonfigurowania powiadomienia.

Poniższy kod przedstawia sposób otwierania zestawu wierszy z obiektu ATL i używania funkcji `AtlAdvise` w celu skonfigurowania ujścia powiadomień. `AtlAdvise` zwraca plik cookie, który jest używany podczas wywoływania `AtlUnadvise`.

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
propset.AddProperty(DBPROP_IConnectionPointContainer, true);
```

Następnie używany przez następujący kod:

```cpp
product.Open(session, _T("Products"), &propset);

AtlAdvise(product.m_spRowset, GetUnknown(), IID_IRowsetNotify, &m_dwCookie);
```

## <a name="see-also"></a>Zobacz też

[Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)
