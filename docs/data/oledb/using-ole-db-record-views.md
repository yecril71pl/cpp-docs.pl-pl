---
title: Korzystanie z widoków rekordów OLE DB | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB record views
- COleDBRecordView class, overview
- rowsets, record views
- record views, record view objects
- OLE DB, record views
- MFC, record views
ms.assetid: 1cd3e595-ce08-43d8-a0a9-d03b5d3e24ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b0b787686fc09d943de030645d56465cd259bc37
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43215770"
---
# <a name="using-ole-db-record-views"></a>Korzystanie z widoków rekordów OLE DB
Jeśli chcesz wyświetlać dane zestawu wierszy OLE DB w aplikacji MFC, należy użyć klasy MFC [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md). Obiekt widoku rekordu utworzone na podstawie `COleDBRecordView` umożliwia wyświetlanie rekordów bazy danych w kontrolkach MFC. W widoku rekordu jest widoku formularza okna dialogowego podłączone bezpośrednio do obiektu wierszy OLE DB utworzone na podstawie `CRowset` klasy szablonu. Uzyskiwanie dojścia do obiektu zestawu wierszy jest prosty:  
  
```cpp  
COleDBRecordView myRecordView;  
...  
// CProductAccessor is a user record class  
CRowset<CAccessor<CProductAccessor>> myRowSet = myRecordView.OnGetRowset();  
```  
  
 W widoku są wyświetlane pola `CRowset` obiektu w oknie dialogowym formanty. `COleDBRecordView` Obiekt używa wymiany danych okna dialogowego (DDX) i wyposażone w funkcję nawigacji `CRowset` (`MoveFirst`, `MoveNext`, `MovePrev`, i `MoveLast`) do automatyzowania przenoszenia danych między formantami na formularzu i pola zestawu wierszy. `COleDBRecordView` śledzi informacje o jego pozycja w zestawie wierszy tak, aby zaktualizować widoku rekordu interfejsu użytkownika i dostarcza [OnMove](../../mfc/reference/coledbrecordview-class.md#onmove) metodą aktualizacji bieżący rekord przed przeniesieniem do innej.  
  
 Można użyć funkcji DDX z `COleDbRecordView` pobieranie danych bezpośrednio z rekordów bazy danych i wyświetlania ich w formantu w oknie dialogowym. Należy używać **funkcje DDX_** <strong>\*</strong> metody (takie jak `DDX_Text`), a nie **funkcje DDX_Field** <strong>\*</strong> funkcje (takie jak `DDX_FieldText`) przy użyciu `COleDbRecordView`.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)   
 [Klasa COleDBRecordView](../../mfc/reference/coledbrecordview-class.md)