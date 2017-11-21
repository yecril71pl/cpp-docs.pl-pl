---
title: "Korzystanie z widoków rekordów OLE DB | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB record views
- COleDBRecordView class, overview
- rowsets, record views
- record views, record view objects
- OLE DB, record views
- MFC, record views
ms.assetid: 1cd3e595-ce08-43d8-a0a9-d03b5d3e24ce
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c4e57f320c8b207e7b1c8721ab25744cd1f128bc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="using-ole-db-record-views"></a>Korzystanie z widoków rekordów OLE DB
Jeśli chcesz wyświetlać dane zestawu wierszy OLE DB w aplikacji MFC, należy użyć klasy MFC [coledbrecordview —](../../mfc/reference/coledbrecordview-class.md). Obiekt widoku rekordu utworzone na podstawie `COleDBRecordView` służy do wyświetlania rekordów bazy danych w kontrolkach MFC. Widok rekordu jest widoku Formularz okna dialogowego podłączone bezpośrednio do obiektu wierszy OLE DB utworzone na podstawie `CRowset` klasy szablonu. Uzyskiwanie dojścia do obiektu zestawu wierszy jest prosty:  
  
```  
COleDBRecordView myRecordView;  
...  
// CProductAccessor is a user record class  
CRowset<CAccessor<CProductAccessor>> myRowSet = myRecordView.OnGetRowset();  
```  
  
 W widoku wyświetlane są pola `CRowset` obiektu w oknie dialogowym formanty. `COleDBRecordView` Obiekt używa wymiany danych okna dialogowego (DDX) i nawigacyjne funkcje wbudowane w `CRowset` (**MoveFirst**, `MoveNext`, `MovePrev`, i `MoveLast`) do automatyzowania przepływu danych między formantami w formularzu i pola zestawu wierszy. `COleDBRecordView`przechowuje informacje o pozycji użytkownika w zestawie wierszy, dzięki czemu widoku rekordu można zaktualizować interfejsu użytkownika i dostaw [OnMove](../../mfc/reference/coledbrecordview-class.md#onmove) metodą aktualizacji dla bieżącego rekordu przed przejściem do innego.  
  
 Możesz użyć funkcji DDX z **coledbrecordview —** Pobierz dane bezpośrednio z rekordów bazy danych i wyświetlić je w formancie okna dialogowego. Należy używać **DDX_\***  metod (takich jak `DDX_Text`), a nie **ddx_field —\***  funkcje (takie jak `DDX_FieldText`) z **coledbrecordview —** .  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)   
 [Coledbrecordview — klasa](../../mfc/reference/coledbrecordview-class.md)