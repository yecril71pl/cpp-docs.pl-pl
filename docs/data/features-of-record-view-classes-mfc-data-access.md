---
title: Funkcje klas widoków rekordów (dostęp do danych MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, classes
- record view classes
ms.assetid: e7b2820f-09c4-483f-83c0-317e8be42bdf
ms.openlocfilehash: 5f8de956065571109c988bd2940d21822bba7cfd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397955"
---
# <a name="features-of-record-view-classes--mfc-data-access"></a>Funkcje klas widoków rekordów (dostęp do danych MFC)

Możecie programowania opartego na formularzach dostępu do danych za pomocą klasy [CFormView](../mfc/reference/cformview-class.md), ale [CRecordView](../mfc/reference/crecordview-class.md) ogólnie jest lepiej klasy pochodzi od. W uzupełnieniu do jego `CFormView` funkcji `CRecordView`:

- Udostępnia wymiana danych okna dialogowego (DDX) między formanty formularza i obiekt skojarzony zestaw rekordów.

- Obsługuje przenieść pierwszy, Przenieś dalej, przenieś poprzednie i przenieść ostatniego polecenia do nawigowania między rekordami w obiekcie skojarzony zestaw rekordów.

- Po użytkownik przejdzie do innego rekordu aktualizacji zmienia się w bieżącym rekordzie.

Aby uzyskać więcej informacji na temat nawigacji zobacz [widoków rekordów: Obsługa nawigacji w widoku rekordu](../data/supporting-navigation-in-a-record-view-mfc-data-access.md).

## <a name="see-also"></a>Zobacz także

[Widoki rekordów (dostęp do danych MFC)](../data/record-views-mfc-data-access.md)<br/>
[Lista sterowników ODBC](../data/odbc/odbc-driver-list.md)