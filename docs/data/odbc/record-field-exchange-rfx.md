---
title: Rejestruj pola programu Exchange (RFX) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- RFX (ODBC) [C++]
- data [MFC], moving between sources and recordsets
- database classes [C++], RFX
- data [MFC]
- ODBC [C++], RFX
ms.assetid: f5ddfbf0-2901-48d7-9848-4fb84de3c7ee
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 50fc0aea1ef50124cd98b0d0498b767d1f00e5c0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="record-field-exchange-rfx"></a>Wymiana pól rekordów (RFX)
Klasy baz danych MFC ODBC zautomatyzować przenoszenie danych między źródłem danych a [rekordów](../../data/odbc/recordset-odbc.md) obiektu. Gdy klasa wyprowadzona z z [crecordset —](../../mfc/reference/crecordset-class.md) i nie należy używać zbiorcze pobieranie z wiersza, dane są przesyłane przez mechanizm pól rekordów (RFX) programu exchange.  
  
> [!NOTE]
>  Jeśli zaimplementowano zbiorcze pobieranie z wiersza w pochodnym `CRecordset` klasy, platformę używa mechanizmu programu exchange (zbiorczego RFX) pól rekordów zbiorczego transferu danych. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 RFX jest podobny do wymiana danych okna dialogowego (DDX). Przenoszenie danych między źródłem danych i elementy członkowskie danych pola rekordów wymaga wielu wywołań do zestawu rekordów [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) funkcji i dużą interakcji między platformę i [ODBC](../../data/odbc/odbc-basics.md). Mechanizm RFX jest bezpieczne i powoduje zapisanie pracy, takich jak wywoływanie funkcji ODBC **:: Procedura SQLBindCol**. Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md).  
  
 RFX przede wszystkim jest niewidoczny dla użytkownika. Jeśli zadeklarować klas rekordów przy użyciu Kreatora aplikacji MFC lub **Dodaj klasę** (zgodnie z opisem w [Dodawanie konsumenta MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)), RFX wbudowaną je automatycznie. Klasy rekordów musi pochodzić od klasy podstawowej `CRecordset` dostarczanych przez platformę. Kreator aplikacji MFC umożliwia tworzenie klasy początkowej zestawu rekordów. **Dodaj klasę** umożliwia dodanie innych klas rekordów w miarę potrzeby. Aby uzyskać dodatkowe informacje i przykłady, zobacz [Dodawanie konsumenta MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).  
  
 Musisz ręcznie dodać małej ilości kodu RFX w trzech przypadkach, gdy chcesz:  
  
-   Użyj sparametryzowanych zapytań. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: parametryzacja zestawu rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
-   Wykonanie sprzężeń (za pomocą jednego zestawu rekordów dla kolumn z dwóch lub więcej tabel). Aby uzyskać więcej informacji, zobacz [zestaw rekordów: wykonywanie Join (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).  
  
-   Dynamiczne powiązanie kolumn danych. Jest to mniej typowych niż parametryzacja. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: dynamiczne wiązanie danych kolumn (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
 Aby uzyskać większą wiedzę RFX, zobacz [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 W poniższych tematach opisano szczegóły przy użyciu obiektów zestaw rekordów:  
  
-   [Wymiana pól rekordów: używanie RFX](../../data/odbc/record-field-exchange-using-rfx.md)  
  
-   [Wymiana pól rekordów: używanie funkcji RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)  
  
-   [Wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Otwórz połączenie z bazą danych (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)   
 [Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Klient MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [Obsługa baz danych, Kreator aplikacji MFC](../../mfc/reference/database-support-mfc-application-wizard.md)   
 [Klasa CRecordset](../../mfc/reference/crecordset-class.md)