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
ms.openlocfilehash: 5aa16d5f2a3a02d0e9fd6bb3dd5de71494e81d4a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-bookmarks"></a>Korzystanie z zakładek
Przed otwarciem zestawu wierszy, należy wskazać dostawcy chcesz używać zakładek. Aby to zrobić, ustaw **DBPROP_BOOKMARKS** właściwości **true** w Twojej właściwości zestawu. Dostawca pobiera zakładki jako kolumny wartości zero, trzeba używać makra specjalnego `BOOKMARK_ENTRY` i `CBookmark` klasy, jeśli używane są statyczne metody dostępu. `CBookmark` to klasa szablonu, gdy argument jest długość w bajtach buforu zakładki. Długość buforu wymagane do zakładki zależy od dostawcy. Jeśli używasz Dostawca ODBC OLE DB, jak pokazano w poniższym przykładzie buforu musi być 4 bajty.  
  
```  
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
  
 Jeśli używasz `CDynamicAccessor`, bufor jest przydzielane dynamicznie w czasie wykonywania. W takim przypadku można użyć specjalna wersja `CBookmark` dla którego nie zostanie określona długość buforu. Użyj funkcji `GetBookmark` pobrać zakładki dla bieżącego rekordu, jak pokazano w tym przykładowym kodzie:  
  
```  
CTable<CDynamicAccessor> product;  
CBookmark<>              bookmark;  
CDBPropSet propset(DBPROPSET_ROWSET);  
  

propset.AddProperty(DBPROP_BOOKMARKS, true);  

product.Open(session, "Products", &propset);  

product.MoveNext();  

product.GetBookmark(&bookmark);  
```  
  
 Informacje dotyczące obsługi zakładki w dostawcach, zobacz [Obsługa dostawców dla zakładek](../../data/oledb/provider-support-for-bookmarks.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)