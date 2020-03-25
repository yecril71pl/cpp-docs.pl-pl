---
title: Korzystanie z istniejącego zestawu rekordów ADO
ms.date: 11/04/2016
helpviewer_keywords:
- ADO recordsets [C++]
- OLE DB consumer templates, ADO recordsets
- recordsets [C++], using in OLE DB
ms.assetid: a9b1de8a-d379-49b1-a26e-578741e9f6a8
ms.openlocfilehash: 48f6eb3bac34b37f495b9492e19b4197ed69cca3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209355"
---
# <a name="using-an-existing-ado-recordset"></a>Korzystanie z istniejącego zestawu rekordów ADO

Aby mieszać OLE DB Szablony konsumentów i obiekty danych aktywnych (ADO), należy użyć obiektów ADO do otwarcia zestawu rekordów (odpowiadającego zestawowi wierszy w szablonach OLE DB konsumentów). W przypadku zestawu rekordów wykonaj następujące czynności, aby nawiązać połączenie z zestawem wierszy OLE DB:

1. Wywołaj `QueryInterface` dla wskaźników `IRowset` i `IAccessor`.

    ```cpp
    IRowset* lpRowset = NULL;
    IAccessor* lpAccessor = NULL;
    lpUnk->QueryInterface(IID_IRowset, (void**)&lpRowset);
    lpUnk->QueryInterface(IID_IAccessor, (void**)&lpAccessor);
    ```

    > [!NOTE]
    > *lpUnk* wskazuje obiekt `IUnknown` zestawu rekordów ADO.

1. Dołącz metodę dostępu i zestaw wierszy do odpowiednich OLE DB klas szablonu użytkownika.

    ```cpp
    CRowset rs;
    CAccessor accessor;

    accessor.AddAccessorInfo(0ul);      // 0 is the ordinal of an ADO accessor
    rs.m_spRowset.Attach(lpRowset);      // use the Attach method of CComPtr<>
    rs.SetAccessor(accessor);
    ```

## <a name="see-also"></a>Zobacz też

[Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)
