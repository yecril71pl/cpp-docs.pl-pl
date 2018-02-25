---
title: "Przy użyciu istniejącego zestawu rekordów ADO | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ADO recordsets [C++]
- OLE DB consumer templates, ADO recordsets
- recordsets [C++], using in OLE DB
ms.assetid: a9b1de8a-d379-49b1-a26e-578741e9f6a8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a819a0f292951060f4dc6b9fdda580db8f0d2127
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="using-an-existing-ado-recordset"></a>Korzystanie z istniejącego zestawu rekordów ADO
Aby utworzyć szablony konsumentów OLE DB i aktywne obiektów ADO (Data), umożliwia otwieranie zestawu rekordów (odpowiadający zestawu wierszy w OLE DB szablony konsumentów) ADO. Jeśli masz zestawu rekordów, wykonaj następujące czynności do nawiązania połączenia zestawu wierszy OLE DB:  
  
1.  Wywołanie `QueryInterface` dla `IRowset` i `IAccessor` wskaźniki.  
  
    ```  
    IRowset* lpRowset = NULL;  
    IAccessor* lpAccessor = NULL;  
    lpUnk->QueryInterface(IID_IRowset, (void**)&lpRowset);  
    lpUnk->QueryInterface(IID_IAccessor, (void**)&lpAccessor);  
    ```  
  
    > [!NOTE]
    >  *lpUnk* wskazuje **IUnknown** obiektu zestawu rekordów ADO.  
  
2.  Dołącz metody dostępu i zestawu wierszy do ich odpowiednich klas szablonów konsumentów OLE DB.  
  
    ```  
    CRowset rs;  
    CAccessor accessor;  
  
    accessor.AddAccessorInfo(0ul);      // 0 is the ordinal of an ADO accessor  
    rs.m_spRowset.Attach(lpRowset);      // use the Attach method of CComPtr<>  
    rs.SetAccessor(accessor);  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)