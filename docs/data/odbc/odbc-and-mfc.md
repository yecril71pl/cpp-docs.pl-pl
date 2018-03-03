---
title: ODBC i MFC | Dokumentacja firmy Microsoft
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
- ODBC [C++], MFC
- connections [C++], databases
- connections [C++], data source
- databases [C++], connecting to
- data sources [C++], connecting to
- MFC [C++], ODBC and
- database connections [C++], MFC ODBC classes
ms.assetid: 98f02fd7-1235-437b-89a9-edfd0fc797f7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 48dd657d4cf1b315b29fda881b949dea29204f24
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-and-mfc"></a>ODBC i MFC
> [!NOTE]
>  Aby korzystać z klasami baz danych MFC, musi mieć odpowiedni sterownik ODBC dla źródła danych. Najnowsza sterownik ODBC firmy Microsoft dla programu SQL Server jest [13 sterownika ODBC firmy Microsoft dla programu SQL Server](https://www.microsoft.com/en-us/download/details.aspx?id=50420). Większość dostawców bazy danych Podaj sterownika ODBC dla systemu Windows. 
  
 W tym temacie główne pojęcia związane z klasami bazy danych opartej na ODBC biblioteki Microsoft Foundation Classes (MFC) i zawiera omówienie sposobu klasy współpracują ze sobą. Aby uzyskać więcej informacji na temat ODBC i MFC zobacz następujące tematy:  
  
-   [Nawiązywanie połączenia ze źródłem danych](connecting-to-a-data-source.md)  
  
-   [Wybieranie rekordów i operowanie nimi](selecting-and-manipulating-records.md)  
  
-   [Wyświetlanie danych w formularzu i operowanie nimi](displaying-and-manipulating-data-in-a-form.md)  
  
-   [Praca z dokumentami i widokami](working-with-documents-and-views.md)  
  
-   [Dostęp do ODBC i SQL](access-to-odbc-and-sql.md)  
  
-   [Dalsze informacje o klasach MFC ODBC](further-reading-about-the-mfc-odbc-classes.md)  
  
 Klasy baz danych MFC ODBC w oparciu mają na celu zapewnienia dostępu do dowolnej bazy danych, dla którego jest dostępny sterownik ODBC. Ponieważ klasy używają ODBC, aplikacji można uzyskać dostępu do danych w wielu formatów danych i różne konfiguracje zdalni lokalnego. Nie trzeba napisać kod specjalny przypadek do obsługi systemów zarządzania innej bazy danych (DBMS). Użytkownicy mają odpowiedni sterownik ODBC dla danych, które chcą uzyskać dostęp, korzystają z programem do manipulowania dane w tabelach przechowywanych.  
  
## <a name="see-also"></a>Zobacz też  
 [Open Database Connectivity (ODBC)](open-database-connectivity-odbc.md)