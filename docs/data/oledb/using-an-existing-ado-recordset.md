---
title: Korzystanie z istniejącego zestawu rekordów ADO
ms.date: 11/04/2016
helpviewer_keywords:
- ADO recordsets [C++]
- OLE DB consumer templates, ADO recordsets
- recordsets [C++], using in OLE DB
ms.assetid: a9b1de8a-d379-49b1-a26e-578741e9f6a8
ms.openlocfilehash: 62e56b818a766bf3b7efddf9243ffd47ad2cb46f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610603"
---
# <a name="using-an-existing-ado-recordset"></a>Korzystanie z istniejącego zestawu rekordów ADO

Aby łączyć, szablony konsumentów OLE DB i aktywne Data Objects (ADO), należy użyć ADO można otworzyć zestawu rekordów (odpowiadających dla zestawu wierszy OLE DB konsumenta szablonów). W przypadku zestawu rekordów, wykonaj następujące polecenie, aby nawiązać połączenie z zestawu wierszy OLE DB:

1. Wywołaj `QueryInterface` dla `IRowset` i `IAccessor` wskaźników.

    ```cpp
    IRowset* lpRowset = NULL;
    IAccessor* lpAccessor = NULL;
    lpUnk->QueryInterface(IID_IRowset, (void**)&lpRowset);
    lpUnk->QueryInterface(IID_IAccessor, (void**)&lpAccessor);
    ```

    > [!NOTE]
    > *lpUnk* wskazuje `IUnknown` obiekt zestawu rekordów ADO.

1. Dołącz metody dostępu i zestawu wierszy do ich odpowiednich klas szablonów konsumentów OLE DB.

    ```cpp
    CRowset rs;
    CAccessor accessor;

    accessor.AddAccessorInfo(0ul);      // 0 is the ordinal of an ADO accessor
    rs.m_spRowset.Attach(lpRowset);      // use the Attach method of CComPtr<>
    rs.SetAccessor(accessor);
    ```

## <a name="see-also"></a>Zobacz też

[Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)