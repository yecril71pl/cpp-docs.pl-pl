---
title: ODBC i MFC
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC [C++], MFC
- connections [C++], databases
- connections [C++], data source
- databases [C++], connecting to
- data sources [C++], connecting to
- MFC [C++], ODBC and
- database connections [C++], MFC ODBC classes
ms.assetid: 98f02fd7-1235-437b-89a9-edfd0fc797f7
ms.openlocfilehash: 94a3455324a52b789bcfcf192b698a3c42b37c00
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213193"
---
# <a name="odbc-and-mfc"></a>ODBC i MFC

> [!NOTE]
>  Aby używać klas baz danych MFC, musisz mieć odpowiedni sterownik ODBC dla źródła danych. Ostatnim sterownikiem Microsoft ODBC dla SQL Server jest [Sterownik Microsoft ODBC Driver 13 dla SQL Server](https://www.microsoft.com/download/details.aspx?id=50420). Większość dostawców baz danych udostępnia sterownik ODBC dla systemu Windows.

W tym temacie przedstawiono główne koncepcje klas baz danych opartych na ODBC biblioteki Microsoft Foundation Classes (MFC) i przedstawiono sposób współdziałania klas. Aby uzyskać więcej informacji na temat ODBC i MFC, zobacz następujące tematy:

- [Nawiązywanie połączenia ze źródłem danych](connecting-to-a-data-source.md)

- [Wybieranie rekordów i operowanie nimi](selecting-and-manipulating-records.md)

- [Wyświetlanie danych w formularzu i operowanie nimi](displaying-and-manipulating-data-in-a-form.md)

- [Praca z dokumentami i widokami](working-with-documents-and-views.md)

- [Dostęp do ODBC i SQL](access-to-odbc-and-sql.md)

- [Dalsze informacje o klasach MFC ODBC](further-reading-about-the-mfc-odbc-classes.md)

Klasy baz danych MFC oparte na ODBC zostały zaprojektowane w celu zapewnienia dostępu do dowolnej bazy danych, dla której dostępny jest sterownik ODBC. Ponieważ klasy używają ODBC, aplikacja może uzyskiwać dostęp do danych w wielu różnych formatach danych i w różnych konfiguracjach lokalnych/zdalnych. Nie trzeba pisać kodu specjalnego przypadku w celu obsługi różnych systemów zarządzania bazami danych (DBMS). Tak długo, jak użytkownicy mają odpowiedni sterownik ODBC dla danych, do których chcą uzyskać dostęp, mogą używać programu do manipulowania danymi w tabelach przechowywanych w tym miejscu.

## <a name="see-also"></a>Zobacz też

[Open Database Connectivity (ODBC)](open-database-connectivity-odbc.md)
