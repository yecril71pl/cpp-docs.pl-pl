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
ms.openlocfilehash: b1c99b8b271b4948584d9bdb25c74518fe835573
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093223"
---
# <a name="features-of-record-view-classes--mfc-data-access"></a>Funkcje klas widoków rekordów (dostęp do danych MFC)

Możecie programowania opartego na formularzach dostępu do danych za pomocą klasy [CFormView](../mfc/reference/cformview-class.md), ale [CRecordView](../mfc/reference/crecordview-class.md) ogólnie jest lepiej klasy pochodzi od. W uzupełnieniu do jego `CFormView` funkcji `CRecordView`:  
  
- Udostępnia wymiana danych okna dialogowego (DDX) między formanty formularza i obiekt skojarzony zestaw rekordów.  
  
- Obsługuje przenieść pierwszy, Przenieś dalej, przenieś poprzednie i przenieść ostatniego polecenia do nawigowania między rekordami w obiekcie skojarzony zestaw rekordów.  
  
- Po użytkownik przejdzie do innego rekordu aktualizacji zmienia się w bieżącym rekordzie.  
  
Aby uzyskać więcej informacji o nawigacji, zobacz [widoków rekordów: Obsługa nawigacji w widoku rekordu](../data/supporting-navigation-in-a-record-view-mfc-data-access.md).  
  
## <a name="see-also"></a>Zobacz też  

[Widoki rekordów (dostęp do danych MFC)](../data/record-views-mfc-data-access.md)<br/>
[Lista sterowników ODBC](../data/odbc/odbc-driver-list.md)