---
title: Otrzymywanie powiadomień | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/24/2018
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
ms.openlocfilehash: 244ebbfdb1ca706550fa26acd29e0af067cb1a7a
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50079717"
---
# <a name="receiving-notifications"></a>Odbieranie powiadomień

OLE DB zawiera interfejsy otrzymywanie powiadomień po wystąpieniu zdarzenia. Te ustawienia zostały opisane w [OLE DB obiektu powiadomienia](/previous-versions/windows/desktop/ms725406) w **OLE DB Podręcznik programisty**. Ustawienia te zdarzenia używa standardowego mechanizmu COM w punkt połączenia. Na przykład obiekt ATL, który chce, aby pobrać zdarzenia za pośrednictwem `IRowsetNotify` implementuje `IRowsetNotify` interfejsu, dodając `IRowsetNotify` Klasa pochodna listy i ujawnienie go za pośrednictwem com_interface_entry — makro.

`IRowsetNotify` ma trzy metody, które mogą być wywoływane w różnym czasie. Jeśli chcesz odpowiedzieć na tylko jeden z tych metod, możesz użyć [irowsetnotifyimpl —](../../data/oledb/irowsetnotifyimpl-class.md) klasy, która zwraca E_NOTIMPL dla metody nie jest zainteresowany.

Podczas tworzenia zestawu wierszy, musisz poinformować dostawcy ma obiektu zwróconego zestawu wierszy, do obsługi `IConnectionPointContainer`, który jest wymagany do skonfigurowania powiadomień.

Poniższy kod przedstawia sposób otwierania zestawu wierszy z obiektu ATL i użyj `AtlAdvise` funkcję, aby skonfigurować obiekt sink powiadomień. `AtlAdvise` Zwraca wartość pliku cookie, który jest używany podczas wywoływania `AtlUnadvise`.

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