---
title: Korzystanie z zakładek
ms.date: 10/24/2018
helpviewer_keywords:
- rowsets, bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- OLE DB providers, bookmark support
ms.assetid: 7fa1d1a8-5063-4aa9-93ee-815bb9c98fae
ms.openlocfilehash: 5a4a2d65ba7367b5568603b5f08a07c6d85cc4a5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209317"
---
# <a name="using-bookmarks"></a>Korzystanie z zakładek

Przed otwarciem zestawu wierszy należy poinformować dostawcę, którego ma używać zakładek. W tym celu ustaw właściwość `DBPROP_BOOKMARKS` na **wartość true** w zestawie właściwości. Dostawca pobiera zakładki jako kolumny zero, dlatego należy użyć specjalnego makra BOOKMARK_ENTRY i klasy `CBookmark`, jeśli używasz statycznej metody dostępu. `CBookmark` jest klasą szablonu, w której argument jest długością w bajtach buforu zakładki. Długość buforu wymaganego dla zakładki zależy od dostawcy. Jeśli używasz dostawcy OLE DB ODBC, jak pokazano w poniższym przykładzie, bufor musi mieć 4 bajty.

```cpp
class CProducts
{
public:
   CBookmark<4> bookmark;

   BEGIN_COLUMN_MAP(CProducts)
      BOOKMARK_ENTRY(bookmark)
   END_COLUMN_MAP()
};
```

Następnie używany przez następujący kod:

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
propset.AddProperty(DBPROP_BOOKMARKS, true);

CTable<CAccessor<CProducts>> product;
CSession session;
product.Open(session, "Products", &propset);
```

Jeśli używasz `CDynamicAccessor`, bufor jest ustawiany dynamicznie w czasie wykonywania. W takim przypadku można użyć wyspecjalizowanej wersji `CBookmark`, dla której nie zostanie określona długość buforu. Użyj `GetBookmark` funkcji, aby pobrać zakładkę z bieżącego rekordu, jak pokazano w tym przykładzie kodu:

```cpp
CTable<CDynamicAccessor> product;
CBookmark<> bookmark;
CDBPropSet propset(DBPROPSET_ROWSET);
CSession session;

propset.AddProperty(DBPROP_BOOKMARKS, true);
product.Open(session, "Products", &propset);
product.MoveNext();
product.GetBookmark(&bookmark);
```

Aby uzyskać informacje na temat obsługi zakładek w dostawcach, zobacz [obsługa dostawców dla zakładek](../../data/oledb/provider-support-for-bookmarks.md).

## <a name="see-also"></a>Zobacz też

[Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)
