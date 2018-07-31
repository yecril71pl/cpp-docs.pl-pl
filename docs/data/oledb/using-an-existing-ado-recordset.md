---
title: Przy użyciu istniejącego zestawu rekordów ADO | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ADO recordsets [C++]
- OLE DB consumer templates, ADO recordsets
- recordsets [C++], using in OLE DB
ms.assetid: a9b1de8a-d379-49b1-a26e-578741e9f6a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: be948293947d4f007d151e4a89e0ff87fc897bbd
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2018
ms.locfileid: "39338941"
---
# <a name="using-an-existing-ado-recordset"></a>Korzystanie z istniejącego zestawu rekordów ADO
Aby łączyć, szablony konsumentów OLE DB i aktywne Data Objects (ADO), należy użyć ADO można otworzyć zestawu rekordów (odpowiadających dla zestawu wierszy OLE DB konsumenta szablonów). W przypadku zestawu rekordów, wykonaj następujące polecenie, aby nawiązać połączenie z zestawu wierszy OLE DB:  
  
1.  Wywołaj `QueryInterface` dla `IRowset` i `IAccessor` wskaźników.  
  
    ```cpp  
    IRowset* lpRowset = NULL;  
    IAccessor* lpAccessor = NULL;  
    lpUnk->QueryInterface(IID_IRowset, (void**)&lpRowset);  
    lpUnk->QueryInterface(IID_IAccessor, (void**)&lpAccessor);  
    ```  
  
    > [!NOTE]
    >  *lpUnk* wskazuje `IUnknown` obiekt zestawu rekordów ADO.  
  
2.  Dołącz metody dostępu i zestawu wierszy do ich odpowiednich klas szablonów konsumentów OLE DB.  
  
    ```cpp  
    CRowset rs;  
    CAccessor accessor;  
  
    accessor.AddAccessorInfo(0ul);      // 0 is the ordinal of an ADO accessor  
    rs.m_spRowset.Attach(lpRowset);      // use the Attach method of CComPtr<>  
    rs.SetAccessor(accessor);  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)