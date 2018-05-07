---
title: Funkcje rekordu wyświetlić klasy (dostęp do danych MFC) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- record views, classes
- record view classes
ms.assetid: e7b2820f-09c4-483f-83c0-317e8be42bdf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9b6717c0ef1167e01df2f5e8de14408b23a9dbb1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="features-of-record-view-classes--mfc-data-access"></a>Funkcje klas widoków rekordów (dostęp do danych MFC)
Możliwość programowania opartej na formularzu dostępu do danych za pomocą klasy [CFormView](../mfc/reference/cformview-class.md), ale [CRecordView](../mfc/reference/crecordview-class.md) jest zazwyczaj pochodzi od klasy lepsze. Oprócz jego `CFormView` funkcje, `CRecordView`:  
  
-   Udostępnia wymiana danych okna dialogowego (DDX) między formantami formularza i obiektów skojarzonych rekordów.  
  
-   Obsługuje Przenieś pierwszy, Przenieś następny Przenieś poprzedniej i Przenieś ostatni poleceń do przechodzenia między rekordy w obiekcie skojarzonych rekordów.  
  
-   Aktualizacje zostanie zmieniona dla bieżącego rekordu, gdy użytkownik przejdzie do innego rekordu.  
  
 Aby uzyskać więcej informacji na temat nawigacji, zobacz [widoków rekordów: Obsługa nawigacji w widoku rekordu](../data/supporting-navigation-in-a-record-view-mfc-data-access.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Widoki rekordów (dostęp do danych MFC)](../data/record-views-mfc-data-access.md)   
 [Lista sterowników ODBC](../data/odbc/odbc-driver-list.md)