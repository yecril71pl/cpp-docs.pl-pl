---
title: Twoja rola w pracy w widokiem rekordu (dostęp do danych MFC) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- record views, customizing default code
- MFC, record views
ms.assetid: 691e89a5-ff21-4ca3-9278-69d4678288bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f0188f9b7498bc704c43f642fcb7aa1dc72af6a4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46105469"
---
# <a name="your-role-in-working-with-a-record-view--mfc-data-access"></a>Twoja rola w pracy w widokiem rekordu (dostęp do danych MFC)

W poniższej tabeli przedstawiono zazwyczaj czynnościom do pracy w widokiem rekordu i struktura jest dla Ciebie.  
  
### <a name="working-with-a-record-view-you-and-the-framework"></a>Pracy w widokiem rekordu: możesz i struktury  
  
|Można|Struktura|  
|---------|-------------------|  
|Edytor Visual C++ okna dialogowego do projektowania formularza.|Umożliwia utworzenie zasobu szablonu okna dialogowego za pomocą kontrolek.|  
|Użyj [Kreator aplikacji MFC](../mfc/reference/database-support-mfc-application-wizard.md) do tworzenia klas pochodnych [CRecordView](../mfc/reference/crecordview-class.md) i [CRecordset](../mfc/reference/crecordset-class.md).|Zapisuje klasy dla Ciebie.|  
|Kontrolki widoku rekordów są mapowane na elementy członkowskie danych pola zestawu rekordów.|Udostępnia DDX między kontrolki i pola zestawu rekordów.|  
||Udostępnia domyślne programy obsługi poleceń do **przenieść pierwszy**, **Przenieś ostatniego**, **Przenieś następny**, i **Przenieś poprzednie** polecenia z menu lub paska narzędzi przyciski.|  
||Aktualizacje zmienia się ze źródłem danych.|  
|[Opcjonalnie] Pisanie kodu w celu wypełnienia pola listy, pola kombi lub inne kontrolki z danymi z drugiego zestawu rekordów.||  
|[Opcjonalnie] Pisanie kodu dla żadnych specjalnych operacji sprawdzania poprawności.||  
|[Opcjonalnie] Pisanie kodu w celu dodawania i usuwania rekordów.||  
  
Programowanie oparte na formularzach jest tylko jedno z podejść do pracy z bazą danych. Aby uzyskać informacje o aplikacji przy użyciu innego interfejsu użytkownika lub bez interfejsu użytkownika, zobacz [MFC: Używanie klas bazy danych z dokumentami i widokami](../data/mfc-using-database-classes-with-documents-and-views.md) i [MFC: przy użyciu klasy bazy danych bez dokumentów i widoków](../data/mfc-using-database-classes-without-documents-and-views.md). W przypadku alternatywnych metod wyświetlania rekordów bazy danych, patrz klasy [CListView](../mfc/reference/clistview-class.md) i [CTreeView](../mfc/reference/ctreeview-class.md).  
  
## <a name="see-also"></a>Zobacz też  

[Widoki rekordów (dostęp do danych MFC)](../data/record-views-mfc-data-access.md)<br/>
[Lista sterowników ODBC](../data/odbc/odbc-driver-list.md)