---
title: Korzystanie z istniejącego zestawu rekordów ADO
ms.date: 11/04/2016
helpviewer_keywords:
- ADO recordsets [C++]
- OLE DB consumer templates, ADO recordsets
- recordsets [C++], using in OLE DB
ms.assetid: a9b1de8a-d379-49b1-a26e-578741e9f6a8
ms.openlocfilehash: eb558bb319bb5ddb61d0383846099d708f99c627
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389011"
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

## <a name="see-also"></a>Zobacz także

[Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)