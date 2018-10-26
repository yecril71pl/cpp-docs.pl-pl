---
title: ODBC i MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b6a712b28fba569bfb46124f828e85dfa5dbb229
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50079509"
---
# <a name="odbc-and-mfc"></a>ODBC i MFC

> [!NOTE]
>  Aby korzystać z klas baz danych MFC, musi mieć odpowiedni sterownik ODBC dla źródła danych. Najpóźniejsza sterownik Microsoft ODBC dla programu SQL Server jest [Microsoft ODBC Driver 13 dla programu SQL Server](https://www.microsoft.com/download/details.aspx?id=50420). Większość dostawców bazy danych Podaj sterownika ODBC dla Windows.

Ten temat wprowadza główne pojęcia biblioteki Microsoft Foundation Classes (MFC) na podstawie ODBC klas baz danych i zawiera omówienie sposobu klasy współpracują ze sobą. Aby uzyskać więcej informacji na temat ODBC i MFC zobacz następujące tematy:

- [Nawiązywanie połączenia ze źródłem danych](connecting-to-a-data-source.md)

- [Wybieranie rekordów i operowanie nimi](selecting-and-manipulating-records.md)

- [Wyświetlanie danych w formularzu i operowanie nimi](displaying-and-manipulating-data-in-a-form.md)

- [Praca z dokumentami i widokami](working-with-documents-and-views.md)

- [Dostęp do ODBC i SQL](access-to-odbc-and-sql.md)

- [Dalsze informacje o klasach MFC ODBC](further-reading-about-the-mfc-odbc-classes.md)

Klasy bazy danych MFC ODBC — na podstawie są przeznaczone do zapewniają dostęp do każdej bazy danych, dla których jest dostępny sterownik ODBC. Ponieważ klasy używają ODBC, aplikacji można uzyskać dostęp do danych w wielu różnych formatów i danych różnych konfiguracjach lokalnych i zdalnych. Nie trzeba napisać kod szczególny do obsługi systemów zarządzania innej bazy danych (DBMS). Użytkownicy mają odpowiedni sterownik ODBC dla danych, które chcą uzyskać dostęp, używają programu można manipulować danymi w tabelach tam przechowywane.

## <a name="see-also"></a>Zobacz też

[Open Database Connectivity (ODBC)](open-database-connectivity-odbc.md)