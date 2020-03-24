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
ms.openlocfilehash: a1645c1116daa66c578a6d6e697ab168e4006af9
ms.sourcegitcommit: eff68e4e82be292a5664616b16a526df3e9d1cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80150956"
---
# <a name="data-access-in-visual-c"></a>Dostęp do danych w programie Visual C++

Praktycznie wszystkie produkty bazy danych, SQL i NoSQL, udostępniają interfejs dla C++ aplikacji natywnych. Standardowym interfejsem w branży jest ODBC, który jest obsługiwany przez wszystkie główne produkty bazy danych SQL i wiele produktów NoSQL. W przypadku produktów innych niż firmy Microsoft skontaktuj się z dostawcą, aby uzyskać więcej informacji. Dostępne są również biblioteki innych firm z różnymi postanowieniami licencyjnymi.

Ze względu na to, że firma 2011 firmy Microsoft włączyła Standard ODBC do łączenia się z bazami danych Microsoft SQL Server, zarówno lokalnie, jak i w chmurze. Aby uzyskać więcej informacji, zobacz [Programowanie dostępu do danych \(MFC-ATL\)](data-access-programming-mfc-atl.md). C++Biblioteki/CLI mogą korzystać z natywnych sterowników ODBC lub ADO.NET. Aby uzyskać więcej informacji, zobacz [dostęp do danych przyC++użyciu usługi ADO.NET (/CLI)](../dotnet/data-access-using-adonet-cpp-cli.md) i [uzyskiwania dostępu do danych w programie Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/accessing-data-in-visual-studio).

## <a name="in-this-section"></a>W tej sekcji

[Programowanie dostępu do danych (MFC/ATL)](data-access-programming-mfc-atl.md)<br/>
Opisuje Programowanie dostępu do danych za pomocą C++wizualizacji, gdzie preferowanym sposobem jest użycie jednej z bibliotek klas, takich jak Biblioteka klas Active Template Library (ATL) lub Biblioteka Microsoft Foundation Class (MFC), która upraszcza pracę z interfejsami API bazy danych.

[Open Database Connectivity (ODBC)](odbc/open-database-connectivity-odbc.md)<br/>
Biblioteka Microsoft Foundation Classes (MFC) dostarcza klasy do programowania za pomocą Open Database Connectivity (ODBC).

[Programowanie OLE DB](oledb/ole-db-programming.md)<br/>
Najbardziej starszy interfejs, który jest nadal wymagany w niektórych scenariuszach, w odniesieniu do programowania na połączonych serwerach.

## <a name="related-topics"></a>Tematy pokrewne

[Nawiązywanie połączenia z SQL Database przy użyciu języka C iC++](/azure/sql-database/sql-database-develop-cplusplus-simple)<br/>
Połącz się z Azure SQL Database z poziomu C++ języka C lub aplikacji.

[Microsoft Azure Storage bibliotekę kliencką dlaC++](https://github.com/Azure/azure-storage-cpp)<br/>
[Usługa Azure Storage](/azure/storage/storage-introduction) to rozwiązanie magazynu w chmurze dla nowoczesnych aplikacji, które polegają na trwałości, dostępności i skalowalności, aby zaspokoić potrzeby klientów. Połącz się z usługą Azure C++ Storage za pomocą biblioteki klienta usługi Azure Storage C++dla programu.

[Sterownik ODBC dla SQL Server](/sql/connect/odbc/microsoft-odbc-driver-for-sql-server)<br/>
Najnowsza wersja sterownika ODBC zapewnia niezawodny dostęp do danych Microsoft SQL Server i Microsoft Azure SQL Database dla aplikacjiC++ opartych na języku C. Zapewnia obsługę funkcji, w tym zawsze szyfrowanych, Azure Active Directory i Zawsze włączone grupy dostępności. Dostępna również dla systemów MacOS i Linux.

[Sterownik OLE DB dla SQL Server](/sql/connect/oledb/oledb-driver-for-sql-server)<br/>
Najnowszym sterownikiem OLE DB jest autonomiczny interfejs programowania aplikacji (API), który obsługuje Microsoft SQL Server i Microsoft Azure SQL Database.

[Microsoft Azure C i C++ Centrum deweloperów](https://azure.microsoft.com/develop/cpp/)<br/>
Platforma Azure ułatwia tworzenie C++ aplikacji o zwiększonej elastyczności, skalowalności i niezawodności przy użyciu ulubionych narzędzi.

[Jak używać Blob Storage zC++](https://docs.microsoft.com/azure/storage/storage-c-plus-plus-how-to-use-blobs)<br/>
Magazyn obiektów blob Azure jest usługą służącą do przechowywania danych niestrukturalnych w chmurze w postaci obiektów blob. Magazyn obiektów blob umożliwia przechowywanie dowolnego typu danych tekstowych lub binarnych, takich jak dokumenty, pliki multimedialne lub instalatory aplikacji. Magazyn obiektów blob jest również nazywany magazynem obiektów.

[Odwołanie do programisty ODBC](https://docs.microsoft.com/sql/odbc/reference/odbc-programmer-s-reference)<br/>
Interfejs ODBC jest przeznaczony do użycia z językiem programowania C. Korzystanie z interfejsu ODBC obejmuje trzy obszary: instrukcje SQL, wywołania funkcji ODBC i programowanie w języku C.

## <a name="see-also"></a>Zobacz też

[Język C++ w programie Visual Studio](../overview/visual-cpp-in-visual-studio.md)
