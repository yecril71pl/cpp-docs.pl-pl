---
title: Korzystanie z zakładek
ms.date: 10/24/2018
helpviewer_keywords:
- rowsets, bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- OLE DB providers, bookmark support
ms.assetid: 7fa1d1a8-5063-4aa9-93ee-815bb9c98fae
ms.openlocfilehash: 8caa33b3bafbaa9e537d9669aa7b60a9355475ef
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218302"
---
# <a name="using-bookmarks"></a>Korzystanie z zakładek

Przed otwarciem zestawu wierszy należy poinformować dostawcę, którego ma używać zakładek. W tym celu należy ustawić `DBPROP_BOOKMARKS` Właściwość na **`true`** wartość w ustawieniu właściwości. Dostawca pobiera zakładki jako kolumny zero, dlatego należy użyć specjalnego makra BOOKMARK_ENTRY i klasy, jeśli używasz `CBookmark` statycznej metody dostępu. `CBookmark`jest klasą szablonu, w której argument jest długością w bajtach buforu zakładki. Długość buforu wymaganego dla zakładki zależy od dostawcy. Jeśli używasz dostawcy OLE DB ODBC, jak pokazano w poniższym przykładzie, bufor musi mieć 4 bajty.

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

Jeśli używasz `CDynamicAccessor` , bufor jest ustawiany dynamicznie w czasie wykonywania. W takim przypadku można użyć wyspecjalizowanej wersji programu, `CBookmark` dla której nie zostanie określona długość buforu. Użyj funkcji, `GetBookmark` Aby pobrać zakładkę z bieżącego rekordu, jak pokazano w tym przykładzie kodu:

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

## <a name="see-also"></a>Zobacz także

[Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)
