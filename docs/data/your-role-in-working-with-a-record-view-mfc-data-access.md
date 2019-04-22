---
title: Twoja rola w pracy w widokiem rekordu (dostęp do danych MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, customizing default code
- MFC, record views
ms.assetid: 691e89a5-ff21-4ca3-9278-69d4678288bb
ms.openlocfilehash: c5c35208f654cff90e3cdf87e697e654bdfbe307
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033008"
---
# <a name="your-role-in-working-with-a-record-view--mfc-data-access"></a>Twoja rola w pracy w widokiem rekordu (dostęp do danych MFC)

W poniższej tabeli przedstawiono zazwyczaj czynnościom do pracy w widokiem rekordu i struktura jest dla Ciebie.

### <a name="working-with-a-record-view-you-and-the-framework"></a>Praca z widoku rekordu: Użytkownik i struktury

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

Programowanie oparte na formularzach jest tylko jedno z podejść do pracy z bazą danych. Aby uzyskać informacje o aplikacji przy użyciu innego interfejsu użytkownika lub bez interfejsu użytkownika, zobacz [MFC: Używanie klas baz danych z dokumentami i widokami](../data/mfc-using-database-classes-with-documents-and-views.md) i [MFC: Używanie klas baz danych bez dokumentów i widoków](../data/mfc-using-database-classes-without-documents-and-views.md). W przypadku alternatywnych metod wyświetlania rekordów bazy danych, patrz klasy [CListView](../mfc/reference/clistview-class.md) i [CTreeView](../mfc/reference/ctreeview-class.md).

## <a name="see-also"></a>Zobacz także

[Widoki rekordów (dostęp do danych MFC)](../data/record-views-mfc-data-access.md)<br/>
[Lista sterowników ODBC](../data/odbc/odbc-driver-list.md)