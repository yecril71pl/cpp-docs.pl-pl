---
title: Zapisz widoki (dostęp do danych MFC) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 89677762fd1744afcb6aa749b374dbbb8301d4c4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029705"
---
# <a name="record-views--mfc-data-access"></a>Widoki rekordów (dostęp do danych MFC)

Ta sekcja dotyczy tylko klas MFC ODBC. Aby uzyskać informacje na temat widoków rekordów OLE DB, zobacz [COleDBRecordView](../mfc/reference/coledbrecordview-class.md) i [przy użyciu OLE DB widoków rekordów](../data/oledb/using-ole-db-record-views.md).  
  
Aby umożliwić obsługę aplikacji opartych na formularzach dostępu do danych, biblioteka klas udostępnia klasę [CRecordView](../mfc/reference/crecordview-class.md). Widoku rekordu jest obiektem widoku formularza formanty są mapowane bezpośrednio do pola danych elementów członkowskich [rekordów](../data/odbc/recordset-odbc.md) obiektu (i pośrednio na odpowiednie kolumny w wyniku zapytania lub tabeli w źródle danych). Takie jak jej klasa bazowa [CFormView](../mfc/reference/cformview-class.md), `CRecordView` zależy od zasobu szablonu okna dialogowego.  
  
## <a name="form-uses"></a>Formularz używa  

Formularze są przydatne w przypadku wielu zadań dostęp do danych:  
  
- Wprowadzanie danych  
  
- Wykonywanie badanie danych tylko do odczytu  
  
- Aktualizowanie danych  
  
## <a name="further-reading-about-record-views"></a>Dalsze informacje o widokach rekordów  

Materiał w tematach dotyczy oparte ODBC i klasy oparte na DAO. Użyj `CRecordView` dla ODBC i `CDaoRecordView` dla DAO.  
  
Tematy obejmują:  
  
- [Funkcje klas widoków rekordów](../data/features-of-record-view-classes-mfc-data-access.md)  
  
- [Wymiana danych dla widoków rekordów](../data/data-exchange-for-record-views-mfc-data-access.md)  
  
- [Twoja rola w pracy w widokiem rekordu](../data/your-role-in-working-with-a-record-view-mfc-data-access.md)  
  
- [Projektowanie i tworzenie widoku rekordu](../data/designing-and-creating-a-record-view-mfc-data-access.md)  
  
- [Używanie widoku rekordu](../data/using-a-record-view-mfc-data-access.md)  
  
## <a name="see-also"></a>Zobacz też  

[Programowanie (MFC/ATL) dostępu do danych](../data/data-access-programming-mfc-atl.md)<br/>
[Lista sterowników ODBC](../data/odbc/odbc-driver-list.md)