---
title: "Dostęp do danych w programie Visual C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 03/28/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Visual C++, data access applications
- databases [C++]
- OLE DB [C++], data access technologies
- data [C++], data access technologies
- data access [C++], class libraries for databases
ms.assetid: 95da6237-bbe2-480a-ae50-3a520051ceff
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9bae9c7d8e50ca12767e5baed436912f04daafd9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="data-access-in-visual-c"></a>Dostęp do danych w programie Visual C++

Prawie wszystkie produkty bazy danych, SQL i NoSQL, zapewniają interfejs do natywnych aplikacji C++. Standardowy interfejs branży jest ODBC, która jest obsługiwana przez wszystkie główne produkty bazy danych SQL i wiele produktów NoSQL. Produkty innych firm można znaleźć dostawcy, aby uzyskać więcej informacji. Dostępne są także biblioteki innej firmy z różnych postanowień licencyjnych.

Ponieważ 2011 Microsoft ma dostosowane ODBC jako standardowe rozwiązanie dla natywnych aplikacji, jak i połączenie z bazami danych programu Microsoft SQL Server, zarówno lokalnie, jak i w chmurze. Aby uzyskać więcej informacji, zobacz [programowania dostępu do danych \(MFC ATL\)](data-access-programming-mfc-atl.md). C + +/ CLI biblioteki użyć sterowników ODBC albo ADO.NET. Aby uzyskać więcej informacji, zobacz [danych dostęp za pomocą ADO.NET (C + +/ CLI)](/dotnet/data-access-using-adonet-cpp-cli.md) i [uzyskiwanie dostępu do danych w programie Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/accessing-data-in-visual-studio).

## <a name="in-this-section"></a>W tej sekcji
[Dane dostępu programowania (MFC/ATL)](data-access-programming-mfc-atl.md) programowania w języku Visual C++ preferowany sposób w przypadku użycia jednej z bibliotek klas takich jak Active szablonu klasy Library (ATL) lub biblioteka Microsoft Foundation Class (MFC), dostęp do starszych danych w tym artykule opisano które upraszczają pracy z bazą danych interfejsów API.

[Otwórz połączenie bazy danych (ODBC)](odbc/open-database-connectivity-odbc.md) biblioteki Microsoft Foundation Classes (MFC) udostępnia klasy dla programowania z otwarte połączenie bazy danych (ODBC).

[OLE DB programowania](oledb/ole-db-programming.md) przede wszystkim starszy interfejs, który jest nadal wymagana w niektórych scenariuszach, w szczególności Programowanie w odniesieniu do połączonych serwerów.

## <a name="related-topics"></a>Tematy pokrewne
[Połącz z bazą danych SQL za pomocą C i C++](/azure/sql-database/sql-database-develop-cplusplus-simple) Połącz z bazą danych SQL Azure z poziomu aplikacji C lub C++.

[Biblioteka klienta usługi Microsoft Azure Storage dla języka C++](https://github.com/Azure/azure-storage-cpp)
[usługi Azure Storage](/azure/storage/storage-introduction) jest rozwiązanie magazynu w chmurze dla nowoczesnych aplikacji, które polegają na trwałości, dostępności i skalowalności, aby zaspokoić potrzeby swoich Klienci. Połączyć się z usługą Azure Storage z C++ za pomocą biblioteki klienta usługi Azure Storage dla języka C++.

[13.1 sterownika ODBC dla programu SQL Server — wydania systemu Windows](https://blogs.msdn.microsoft.com/sqlnativeclient/2016/08/01/announcing-the-odbc-driver-13-1-for-sql-server) najnowszy sterownik ODBC zapewnia dostęp do danych niezawodne do firmy Microsoft SQL Server 2016 Microsoft Azure bazy danych SQL dla aplikacji opartych na języku C/C++. Zapewnia obsługę funkcji, w tym zawsze zaszyfrowane, Azure Active Directory i zawsze włączone grupy dostępności. Również dostępne dla MacOS i Linux.     
 
[SQL Server Native Client](https://msdn.microsoft.com/library/ms130892.aspx) SQL Server Native Client jest danych autonomicznej dostępu interfejsu programowania aplikacji (API), używana dla OLE DB i ODBC, która obsługuje program SQL Server 2005 za pomocą programu SQL Server 2014. Nowe aplikacje powinny używać 13.1 sterownika ODBC dla programu SQL Server.

[Microsoft Azure C i C++ w Centrum deweloperów](https://azure.microsoft.com/develop/cpp/) Azure ułatwia tworzenie aplikacji C++ z większą elastyczność, skalowalność i niezawodność przy użyciu narzędzia do siebie.    

[Jak używać magazynu obiektów Blob w języku C++](https://docs.microsoft.com/azure/storage/storage-c-plus-plus-how-to-use-blobs) magazynu obiektów Blob Azure to usługa, która przechowywania danych niestrukturalnych w chmurze w postaci obiektów blob. Magazyn obiektów blob umożliwia przechowywanie dowolnego typu tekstu lub danych binarnych, takich jak dokument, plik multimedialny lub Instalator aplikacji. Magazyn obiektów blob jest również nazywany magazynem obiektów.

[Podręcznik programisty ODBC](https://docs.microsoft.com/sql/odbc/reference/odbc-programmer-s-reference) interfejsu ODBC jest przeznaczony do użytku z język programowania C. Korzystanie z interfejsu ODBC obejmuje trzy obszary: instrukcji SQL, ODBC działanie wywołań i programowania w języku C.

## <a name="see-also"></a>Zobacz też
[Visual C++](../visual-cpp-in-visual-studio.md)
