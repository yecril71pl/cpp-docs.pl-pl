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
ms.openlocfilehash: 38a625c73a17ecae4d8adc61e8c56bc4bdda67f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320075"
---
# <a name="odbc-and-mfc"></a>ODBC i MFC

> [!NOTE]
> Aby użyć klas bazy danych MFC, musisz mieć odpowiedni sterownik ODBC dla źródła danych. Ostatnim sterownikiem Microsoft ODBC dla programu SQL Server jest [sterownik OdBC firmy Microsoft 13 dla programu SQL Server.](https://www.microsoft.com/download/details.aspx?id=50420) Większość dostawców baz danych udostępnia sterownik ODBC dla systemu Windows.

W tym temacie przedstawiono główne pojęcia klasy bazy danych oparte na odbc biblioteki Programu Microsoft Foundation (MFC) i zawiera omówienie sposobu współpracy klas. Aby uzyskać więcej informacji na temat ODBC i MFC, zobacz następujące tematy:

- [Łączenie się ze źródłem danych](connecting-to-a-data-source.md)

- [Wybieranie rekordów i operowanie nimi](selecting-and-manipulating-records.md)

- [Wyświetlanie i manipulowanie danymi w formularzu](displaying-and-manipulating-data-in-a-form.md)

- [Praca z dokumentami i widokami](working-with-documents-and-views.md)

- [Dostęp do ODBC i SQL](access-to-odbc-and-sql.md)

- [Dalsze informacje o klasach MFC ODBC](further-reading-about-the-mfc-odbc-classes.md)

Klasy bazy danych MFC oparte na odbc są przeznaczone do zapewnienia dostępu do dowolnej bazy danych, dla których sterownik ODBC jest dostępny. Ponieważ klasy używają ODBC, aplikacja może uzyskać dostęp do danych w wielu różnych formatach danych i różnych konfiguracjach lokalnych/zdalnych. Nie trzeba pisać kodu specjalnego przypadku do obsługi różnych systemów zarządzania bazami danych (DBMSs). Tak długo, jak użytkownicy mają odpowiedni sterownik ODBC dla danych, które chcą uzyskać dostęp, mogą używać programu do manipulowania danymi w tabelach tam przechowywanych.

## <a name="see-also"></a>Zobacz też

[Łączność z otwartą bazą danych (ODBC)](open-database-connectivity-odbc.md)
