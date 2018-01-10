---
title: "Twoja rola w pracy w widokiem rekordu (dostęp do danych MFC) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- record views, customizing default code
- MFC, record views
ms.assetid: 691e89a5-ff21-4ca3-9278-69d4678288bb
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 03d64715f3bdfb6028fdb039451d4b4b004a059e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="your-role-in-working-with-a-record-view--mfc-data-access"></a>Twoja rola w pracy w widokiem rekordu (dostęp do danych MFC)
W poniższej tabeli przedstawiono co należy zwykle wykonać do pracy w widokiem rekordu i ramach jest dla Ciebie.  
  
### <a name="working-with-a-record-view-you-and-the-framework"></a>Praca z widoku rekordu: użytkownik i struktura  
  
|Można|Platformę|  
|---------|-------------------|  
|Edytor programu Visual C++ okna dialogowego do projektowania formularza.|Tworzy okno dialogowe zasobu szablon z formantami.|  
|Użyj [Kreator aplikacji MFC](../mfc/reference/database-support-mfc-application-wizard.md) do tworzenia klas pochodnych [CRecordView](../mfc/reference/crecordview-class.md) i [crecordset —](../mfc/reference/crecordset-class.md).|Zapisuje klasy dla Ciebie.|  
|Formanty widoku rekordu są mapowane na elementy członkowskie danych pola rekordów.|Udostępnia DDX między formantami a pól rekordów.|  
||Udostępnia domyślne programy obsługi poleceń dla **Przenieś pierwszy**, **Przenieś ostatni**, **Przenieś następny**, i **Przenieś poprzedniej** poleceń z menu lub pasek narzędzi przyciski.|  
||Aktualizacje zmienia się ze źródłem danych.|  
|[Opcjonalnie] Napisać kod do wypełnienia pola listy, pola kombi lub inne formanty z danymi z drugiego zestawu wierszy.||  
|[Opcjonalnie] Pisanie kodu dla żadnych specjalnych operacji sprawdzania poprawności.||  
|[Opcjonalnie] Napisać kod, aby dodawać lub usuwać rekordy.||  
  
 Programowanie oparte na formularzu jest tylko jeden podejście do pracy z bazą danych. Aby uzyskać informacje o aplikacji przy użyciu innych interfejsu użytkownika lub bez interfejsu użytkownika, zobacz [MFC: przy użyciu klasy baz danych z dokumentami i widokami](../data/mfc-using-database-classes-with-documents-and-views.md) i [MFC: przy użyciu klasy bazy danych bez dokumentów i widoków](../data/mfc-using-database-classes-without-documents-and-views.md). Dla alternatywnych metod do wyświetlania rekordów bazy danych, zobacz klasy [clistview —](../mfc/reference/clistview-class.md) i [CTreeView —](../mfc/reference/ctreeview-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Widoki rekordów (dostęp do danych MFC)](../data/record-views-mfc-data-access.md)   
 [Lista sterowników ODBC](../data/odbc/odbc-driver-list.md)