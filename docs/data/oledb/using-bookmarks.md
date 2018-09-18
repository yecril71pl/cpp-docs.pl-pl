---
title: Korzystanie z zakładek | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 8643b8150f08191fa041107fa4a88e3cbcf2964a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042263"
---
# <a name="using-bookmarks"></a>Korzystanie z zakładek

Zanim utworzysz zestaw wierszy, musisz poinformować dostawcę chcesz używać zakładek. Aby to zrobić, należy ustawić `DBPROP_BOOKMARKS` właściwości **true** we właściwości Twojego zestawu. Dostawca pobiera zakładek jako kolumny wartości zero, więc należy użyć makro specjalne BOOKMARK_ENTRY i `CBookmark` klasy, jeśli używane są statyczne metody dostępu. `CBookmark` jest klasą szablonu, gdy argument jest długość w bajtach buforu zakładki. Długość buforu wymaganych do zakładki, zależy od dostawcy. Jeśli używasz dostawcy ODBC OLE DB, jak pokazano w poniższym przykładzie, rozmiar buforu musi być 4 bajty.  
  
```cpp  
class CProducts  
{  
public:  
   CBookmark<4>   bookmark;  
  
   BEGIN_COLUMN_MAP(CProducts)  
      BOOKMARK_ENTRY(bookmark)  
   END_COLUMN_MAP()  
};  
  
CDBPropSet propset(DBPROPSET_ROWSET);  

propset.AddProperty(DBPROP_BOOKMARKS, true);  
  

CTable<CAccessor<CProducts>> product;  
product.Open(session, "Products", &propset);  
```  
  
Jeśli używasz `CDynamicAccessor`, rozmiar buforu jest przydzielany dynamicznie w czasie wykonywania. W takim przypadku można użyć wersji specjalistycznej metody `CBookmark` dla której nie zostanie określona długość buforu. Użyj funkcji `GetBookmark` można pobrać z bieżącego rekordu zakładki, jak pokazano w tym przykładowym kodzie:  
  
```cpp  
CTable<CDynamicAccessor> product;  
CBookmark<>              bookmark;  
CDBPropSet propset(DBPROPSET_ROWSET);  
  

propset.AddProperty(DBPROP_BOOKMARKS, true);  

product.Open(session, "Products", &propset);  

product.MoveNext();  

product.GetBookmark(&bookmark);  
```  
  
Aby dowiedzieć się, jak obsługa zakładek w dostawcy, zobacz [Obsługa dostawców dla zakładek](../../data/oledb/provider-support-for-bookmarks.md).  
  
## <a name="see-also"></a>Zobacz też  

[Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)