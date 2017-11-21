---
title: "Przy użyciu istniejącego zestawu rekordów ADO | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ADO recordsets [C++]
- OLE DB consumer templates, ADO recordsets
- recordsets [C++], using in OLE DB
ms.assetid: a9b1de8a-d379-49b1-a26e-578741e9f6a8
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6331bd40cd65fb7b367a3958aa4fb00a2f123958
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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