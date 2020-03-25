---
title: Funkcje klas widoków rekordów (dostęp do danych MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, classes
- record view classes
ms.assetid: e7b2820f-09c4-483f-83c0-317e8be42bdf
ms.openlocfilehash: 62597a3eb3f7a7e779ca57c9781565176df568d4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213437"
---
# <a name="features-of-record-view-classes--mfc-data-access"></a>Funkcje klas widoków rekordów (dostęp do danych MFC)

Można tworzyć oparte na formularzach Programowanie dostępu do danych za pomocą klasy [CFormView](../mfc/reference/cformview-class.md), ale [formularzy CRecordView](../mfc/reference/crecordview-class.md) jest ogólnie lepszym rozwiązaniem dla klasy. Oprócz funkcji `CFormView` `CRecordView`:

- Udostępnia wymianę danych okna dialogowego (DDX) między kontrolkami formularzy i skojarzonym obiektem zestawu rekordów.

- Obsługuje najpierw przenoszenie, przenoszenie dalej, przenoszenie poprzedniego i przenoszenie ostatnich poleceń w celu nawigowania po rekordach w skojarzonym obiekcie zestawu rekordów.

- Aktualizuje zmiany w bieżącym rekordzie, gdy użytkownik przejdzie do innego rekordu.

Aby uzyskać więcej informacji na temat nawigacji, zobacz [widoki rekordów: obsługa nawigacji w widoku rekordu](../data/supporting-navigation-in-a-record-view-mfc-data-access.md).

## <a name="see-also"></a>Zobacz też

[Widoki rekordów (dostęp do danych MFC)](../data/record-views-mfc-data-access.md)<br/>
[Lista sterowników ODBC](../data/odbc/odbc-driver-list.md)
