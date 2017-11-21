---
title: "Funkcje rekordu wyświetlić klasy (dostęp do danych MFC) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- record views, classes
- record view classes
ms.assetid: e7b2820f-09c4-483f-83c0-317e8be42bdf
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d1a30742a538d941220cf099c33445089c9a907c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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