---
title: Dostęp do danych w programie Visual C++
ms.date: 03/28/2017
helpviewer_keywords:
- Visual C++, data access applications
- databases [C++]
- OLE DB [C++], data access technologies
- data [C++], data access technologies
- data access [C++], class libraries for databases
ms.assetid: 95da6237-bbe2-480a-ae50-3a520051ceff
ms.openlocfilehash: 42c36259b14a7f0341e383bb3a7f2760bab165aa
ms.sourcegitcommit: fcc3aeb271449f8be80348740cffef39ba543407
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2020
ms.locfileid: "82538595"
---
# <a name="data-access-in-visual-c"></a>Dostęp do danych w programie Visual C++

Praktycznie wszystkie produkty bazy danych, SQL i NoSQL, udostępniają interfejs natywnych aplikacji C++. Standardowym interfejsem w branży jest ODBC, który jest obsługiwany przez wszystkie główne produkty bazy danych SQL i wiele produktów NoSQL. W przypadku produktów innych niż firmy Microsoft skontaktuj się z dostawcą, aby uzyskać więcej informacji. Dostępne są również biblioteki innych firm z różnymi postanowieniami licencyjnymi.

Ze względu na to, że firma 2011 firmy Microsoft włączyła Standard ODBC do łączenia się z bazami danych Microsoft SQL Server, zarówno lokalnie, jak i w chmurze. Aby uzyskać więcej informacji, zobacz [programowanie \(dostępu do danych MFC\)-ATL](data-access-programming-mfc-atl.md). Biblioteki C++/CLI mogą korzystać z natywnych sterowników ODBC lub ADO.NET. Aby uzyskać więcej informacji, zobacz [dostęp do danych za pomocą ADO.NET (C++/CLI)](../dotnet/data-access-using-adonet-cpp-cli.md) i [Uzyskiwanie dostępu do danych w programie Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/accessing-data-in-visual-studio).

## <a name="in-this-section"></a>W tej sekcji

[Programowanie dostępu do danych (MFC/ATL)](data-access-programming-mfc-atl.md)<br/>
Opisuje starsze Programowanie dostępu do danych za pomocą Visual C++, w którym preferowanym sposobem jest użycie jednej z bibliotek klas, takich jak Biblioteka klas Active Template Library (ATL) lub Biblioteka Microsoft Foundation Class (MFC), która upraszcza pracę z interfejsami API bazy danych.

[Open Database Connectivity (ODBC)](odbc/open-database-connectivity-odbc.md)<br/>
Biblioteka Microsoft Foundation Classes (MFC) dostarcza klasy do programowania za pomocą Open Database Connectivity (ODBC).

[Programowanie OLE DB](oledb/ole-db-programming.md)<br/>
Najbardziej starszy interfejs, który jest nadal wymagany w niektórych scenariuszach, w odniesieniu do programowania na połączonych serwerach.

## <a name="related-topics"></a>Tematy pokrewne

[Nawiązywanie połączenia z SQL Database przy użyciu języka C i C++](/azure/sql-database/sql-database-develop-cplusplus-simple)<br/>
Połącz się z Azure SQL Database z aplikacji C lub C++.

[Microsoft Azure Storage Biblioteka kliencka dla języka C++](https://github.com/Azure/azure-storage-cpp)<br/>
[Usługa Azure Storage](/azure/storage/common/storage-introduction) to rozwiązanie magazynu w chmurze dla nowoczesnych aplikacji, które polegają na trwałości, dostępności i skalowalności, aby zaspokoić potrzeby klientów. Połącz się z usługą Azure Storage z poziomu języka C++ przy użyciu biblioteki klienta usługi Azure Storage dla języka C++.

[Sterownik ODBC dla SQL Server](/sql/connect/odbc/microsoft-odbc-driver-for-sql-server)<br/>
Najnowsza wersja sterownika ODBC zapewnia niezawodny dostęp do danych Microsoft SQL Server i Microsoft Azure SQL Database dla aplikacji opartych na języku C/C++. Zapewnia obsługę funkcji, w tym zawsze szyfrowanych, Azure Active Directory i Zawsze włączone grupy dostępności. Dostępna również dla systemów MacOS i Linux.

[Sterownik OLE DB dla SQL Server](/sql/connect/oledb/oledb-driver-for-sql-server)<br/>
Najnowszym sterownikiem OLE DB jest autonomiczny interfejs programowania aplikacji (API), który obsługuje Microsoft SQL Server i Microsoft Azure SQL Database.

[Centrum deweloperów Microsoft Azure C i C++](https://azure.microsoft.com/develop/cpp/)<br/>
Platforma Azure ułatwia tworzenie aplikacji w języku C++ o zwiększonej elastyczności, skalowalności i niezawodności przy użyciu ulubionych narzędzi.

[Jak używać Blob Storage z C++](https://docs.microsoft.com/azure/storage/storage-c-plus-plus-how-to-use-blobs)<br/>
Magazyn obiektów blob Azure jest usługą służącą do przechowywania danych niestrukturalnych w chmurze w postaci obiektów blob. Magazyn obiektów blob umożliwia przechowywanie dowolnego typu danych tekstowych lub binarnych, takich jak dokumenty, pliki multimedialne lub instalatory aplikacji. Magazyn obiektów blob jest również nazywany magazynem obiektów.

[Odwołanie do programisty ODBC](https://docs.microsoft.com/sql/odbc/reference/odbc-programmer-s-reference)<br/>
Interfejs ODBC jest przeznaczony do użycia z językiem programowania C. Korzystanie z interfejsu ODBC obejmuje trzy obszary: instrukcje SQL, wywołania funkcji ODBC i programowanie w języku C.

## <a name="see-also"></a>Zobacz także

[C++ w programie Visual Studio](../overview/visual-cpp-in-visual-studio.md)
