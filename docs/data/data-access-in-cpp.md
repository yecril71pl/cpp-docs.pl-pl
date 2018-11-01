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
ms.openlocfilehash: 4bb7c4ecbeba76dcd5a6f1de64fa468d0b8e0854
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635724"
---
# <a name="data-access-in-visual-c"></a>Dostęp do danych w programie Visual C++

Praktycznie wszystkich produktów bazy danych, SQL i NoSQL, zapewniają interfejs do natywnych aplikacji w języku C++. Standardowy interfejs branży jest ODBC, który jest obsługiwany przez wszystkie główne produkty bazy danych SQL i wielu produktów NoSQL. Dla produktów firmy Microsoft zapoznaj się z dostawcą, aby uzyskać więcej informacji. Dostępne są również biblioteki innej firmy z różnych postanowień licencyjnych.

Od 2011 roku Microsoft ma dostosowane ODBC jako standardowe rozwiązanie dla natywnych aplikacji do procesu łączenia bazy danych programu Microsoft SQL Server — zarówno lokalnie, jak i w chmurze. Aby uzyskać więcej informacji, zobacz [programowanie dostępu do danych \(MFC-ATL\)](data-access-programming-mfc-atl.md). C + +/ bibliotek interfejsu wiersza polecenia można używać sterowników ODBC lub ADO.NET. Aby uzyskać więcej informacji, zobacz [ADO.NET za pomocą dostępu do danych (C + +/ CLI)](/dotnet/data-access-using-adonet-cpp-cli.md) i [uzyskiwanie dostępu do danych w programie Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/accessing-data-in-visual-studio).

## <a name="in-this-section"></a>W tej sekcji

[Programowanie (MFC/ATL) dostępu do danych](data-access-programming-mfc-atl.md)<br/>
W tym artykule opisano dostępu starszych danych do programowania w języku Visual C++, gdzie jest preferowany sposób użycia jednej z bibliotek klasy takie jak Active Template klasy Library (ATL) lub biblioteki Microsoft Foundation Class (MFC), które upraszczają pracę z interfejsami API bazy danych.

[Open Database Connectivity (ODBC)](odbc/open-database-connectivity-odbc.md)<br/>
Biblioteka Microsoft Foundation Classes (MFC) dostarcza klas do programowania z Open Database Connectivity (ODBC).

[Programowanie OLE DB](oledb/ole-db-programming.md)<br/>
Przede wszystkim starszy interfejs, który jest nadal wymagana w niektórych scenariuszach, w szczególności w przypadku, gdy są Programowanie w odniesieniu do serwerów połączonych.

## <a name="related-topics"></a>Tematy pokrewne

[Nawiązać połączenie z bazą danych SQL przy użyciu języka C i C++](/azure/sql-database/sql-database-develop-cplusplus-simple)<br/>
Połączyć z usługą Azure SQL Database z aplikacji języka C lub C++.

[Biblioteki klienta usługi Microsoft Azure Storage dla języka C++](https://github.com/Azure/azure-storage-cpp)<br/>
[Usługa Azure Storage](/azure/storage/storage-introduction) to rozwiązanie magazynu w chmurze dla nowoczesnych aplikacji, które polegają na trwałości, dostępności i skalowalności, aby spełniać potrzeby klientów. Nawiąż połączenie usługi Azure Storage z C++ przy użyciu biblioteki klienta usługi Azure Storage dla języka C++.

[Sterownik ODBC 13.1 dla programu SQL Server — Windows wydana](https://blogs.msdn.microsoft.com/sqlnativeclient/2016/08/01/announcing-the-odbc-driver-13-1-for-sql-server)<br/>
Najnowszy sterownik ODBC zapewnia niezawodny dostęp do programu Microsoft SQL Server 2016 Microsoft Azure SQL Database dla języka C/C++, na podstawie aplikacji. Zapewnia obsługę funkcji, w tym z funkcji zawsze zaszyfrowane, usługi Azure Active Directory i zawsze włączonych grup dostępności. Również dostępne w systemach MacOS i Linux.

[SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client-programming)<br/>
SQL Server Native Client jest autonomicznym danych dostęp do interfejsu programowania aplikacji (API), używane dla OLE DB i ODBC, który obsługuje program SQL Server 2005 za pomocą programu SQL Server 2014. Nowe aplikacje powinny używać 13.1 sterownika ODBC dla programu SQL Server.

[Centrum deweloperów języka C++ i C platformy Microsoft Azure](https://azure.microsoft.com/develop/cpp/)<br/>
Azure ułatwia tworzenie aplikacji w języku C++ z większą elastyczność, skalowalności i niezawodności za pomocą dobrze znanych narzędzi.

[Jak używać magazynu obiektów Blob w języku C++](https://docs.microsoft.com/azure/storage/storage-c-plus-plus-how-to-use-blobs)<br/>
Usługa Azure Blob storage to usługa, która przechowuje dane niestrukturalne w chmurze w postaci obiektów blob. Magazyn obiektów blob można przechowywać dowolnego typu dane tekstowe lub binarne, takie jak dokument, plik multimedialny lub Instalator aplikacji. Magazyn obiektów blob jest również określany jako magazyn obiektów.

[ Dokumentacja dotycząca ODBC](https://docs.microsoft.com/sql/odbc/reference/odbc-programmer-s-reference)<br/>
Interfejsu ODBC jest przeznaczony do użytku z języka programowania C. Korzystanie z interfejsu ODBC obejmuje trzy obszary: instrukcje SQL, ODBC wywołania funkcji gromadzenia i programowania C.

## <a name="see-also"></a>Zobacz też

[Visual C++](../visual-cpp-in-visual-studio.md)
