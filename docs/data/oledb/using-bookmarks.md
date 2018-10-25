---
title: Korzystanie z zakładek | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/24/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- rowsets, bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- OLE DB providers, bookmark support
ms.assetid: 7fa1d1a8-5063-4aa9-93ee-815bb9c98fae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6eeb2b6d0c9aa82a6304225b4de14c4d387bfc96
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50072177"
---
# <a name="using-bookmarks"></a>Korzystanie z zakładek

Zanim utworzysz zestaw wierszy, musisz poinformować dostawcę chcesz używać zakładek. Aby to zrobić, należy ustawić `DBPROP_BOOKMARKS` właściwości **true** we właściwości Twojego zestawu. Dostawca pobiera zakładek jako kolumny wartości zero, więc należy użyć makro specjalne BOOKMARK_ENTRY i `CBookmark` klasy, jeśli używasz statycznej metody dostępu. `CBookmark` jest klasą szablonu, gdy argument jest długość w bajtach buforu zakładki. Długość buforu wymaganych do zakładki, zależy od dostawcy. Jeśli używasz dostawcy ODBC OLE DB, jak pokazano w poniższym przykładzie, rozmiar buforu musi być 4 bajty.

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

Jeśli używasz `CDynamicAccessor`, rozmiar buforu jest ustawiane dynamicznie w czasie wykonywania. W takim przypadku można użyć wersji specjalistycznej metody `CBookmark` dla której nie zostanie określona długość buforu. Użyj funkcji `GetBookmark` można pobrać z bieżącego rekordu zakładki, jak pokazano w tym przykładowym kodzie:

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

Aby dowiedzieć się, jak obsługa zakładek w dostawcy, zobacz [Obsługa dostawców dla zakładek](../../data/oledb/provider-support-for-bookmarks.md).

## <a name="see-also"></a>Zobacz też

[Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)