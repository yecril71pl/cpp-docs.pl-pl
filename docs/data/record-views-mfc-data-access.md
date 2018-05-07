---
title: Zarejestruj widoków (MFC Data Access) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], record views
- ODBC recordsets [C++], record views
- databases [C++], record views
- record views [C++]
- forms [C++], data access tasks
ms.assetid: 562122d9-01d8-4284-acf6-ea109ab0408d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 742866b2b11811ee37365ee6cc5e4d3aa881db91
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="record-views--mfc-data-access"></a>Widoki rekordów (dostęp do danych MFC)
Ta sekcja dotyczy tylko dla klas MFC ODBC. Aby uzyskać informacje na temat widoków rekordów OLE DB, zobacz [coledbrecordview —](../mfc/reference/coledbrecordview-class.md) i [przy użyciu OLE DB widoków rekordów](../data/oledb/using-ole-db-record-views.md).  
  
 Aby umożliwić obsługę aplikacji opartej na formularzu dostępu do danych, biblioteki klas udostępnia klasę [CRecordView](../mfc/reference/crecordview-class.md). Widoku rekordu jest obiektem widoku formularza formanty są mapowane bezpośrednio do elementów członkowskich danych pola [rekordów](../data/odbc/recordset-odbc.md) obiektu (i pośrednio na odpowiednie kolumny w tabeli w źródle danych lub wynik kwerendy). Takie jak jej klasa podstawowa [CFormView](../mfc/reference/cformview-class.md), `CRecordView` opiera się na zasobu szablonu okna dialogowego.  
  
## <a name="form-uses"></a>Formularz używa  
 Formularze są przydatne do różnych zadań dostępu do danych:  
  
-   Wprowadzanie danych  
  
-   Wykonywanie badanie danych tylko do odczytu  
  
-   Aktualizowanie danych  
  
## <a name="further-reading-about-record-views"></a>Dalsze informacje na temat widoków rekordów  
 Materiał w tematach dotyczy oparta ODBC i klasy oparte na DAO. Użyj `CRecordView` dla ODBC i `CDaoRecordView` dla DAO.  
  
 Tematy obejmują:  
  
-   [Funkcje klas widoków rekordów](../data/features-of-record-view-classes-mfc-data-access.md)  
  
-   [Wymiana danych dla widoków rekordów](../data/data-exchange-for-record-views-mfc-data-access.md)  
  
-   [Twoja rola w pracy w widokiem rekordu](../data/your-role-in-working-with-a-record-view-mfc-data-access.md)  
  
-   [Projektowanie i tworzenie widoku rekordu](../data/designing-and-creating-a-record-view-mfc-data-access.md)  
  
-   [Używanie widoku rekordu](../data/using-a-record-view-mfc-data-access.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Dostęp do danych programowania (MFC/ATL)](../data/data-access-programming-mfc-atl.md)   
 [Lista sterowników ODBC](../data/odbc/odbc-driver-list.md)