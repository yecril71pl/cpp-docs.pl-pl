---
title: Dostęp do danych programowania (MFC-ATL)
ms.date: 11/16/2018
helpviewer_keywords:
- MFC [C++], data access applications
- databases [C++], MFC
- OLE DB [C++], data access technologies
- data [C++], data access technologies
- data access [C++], class libraries for databases
ms.assetid: def97b2c-b5a6-445f-afeb-308050fd4852
ms.openlocfilehash: b4f5fb6ed21fb23195af340c8de3ee7c654f7fee
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037834"
---
# <a name="data-access-programming-mfcatl"></a>Programowanie (MFC/ATL) dostępu do danych

W ciągu lat Visual C++ udostępnia kilka metod do pracy z bazami danych. W 2011 r. Firma Microsoft ogłosiła, że jest ona wyrównywanie na ODBC jako preferowaną technologię do uzyskiwania dostępu do produktów SQL Server z kodu natywnego. ODBC jest standardem branżowym, a za jej pomocą uzyskasz uzyskania maksymalnej przenośności kodu na wielu platformach i źródeł danych. Większość produktów bazy danych SQL i wielu produktów NoSQL obsługują ODBC. Można użyć ODBC bezpośrednio, wywołując niskiego poziomu interfejsy API ODBC lub można użyć klasy otoki MFC ODBC lub innej biblioteki otoki języka C++.

OLE DB to interfejs API niskiego poziomu, wysokiej wydajności na podstawie specyfikacji modelu COM i jest obsługiwane tylko dla Windows. Użyj OLE DB, jeśli program uzyskuje dostęp do [serwery połączone](/sql/relational-databases/linked-servers/linked-servers-database-engine). ATL zawiera szablony OLE DB, które ułatwiają tworzenie niestandardowych dostawców OLE DB i konsumentów. Najbardziej aktualną wersję OLE DB dostarczane w macierzystym 11 klienta SQL.

## <a name="porting-data-applications"></a>Przenoszenie aplikacji danych

Jeśli starszych aplikacji używa mechanizmu OLE DB lub wyższego poziomu interfejs ADO nawiązać połączenia z programem SQL Server, a nie uzyskujesz dostęp do połączonych serwerów, należy rozważyć Migrowanie do ODBC w niedalekiej przyszłości. Jeśli nie potrzebujesz między platformami lub najnowszych funkcji programu SQL Server, prawdopodobnie umożliwia dostawcy Microsoft OLE DB dla ODBC (MSDASQL).  MSDASQL umożliwia aplikacji, które są oparte na OLE DB i ADO (który jest używany wewnętrznie OLEDB) na dostęp do źródła danych za pośrednictwem sterownika ODBC. Podobnie jak w przypadku dowolnej warstwie tłumaczenia MSDASQL może wpłynąć na wydajność bazy danych. Należy sprawdzić, czy wpływ jest istotne dla twojej aplikacji. MSDASQL jest dostarczana z systemem operacyjnym Windows i Windows Server 2008 i Windows Vista z dodatkiem SP1 to Windows pierwszego wydania do uwzględnienia z 64-bitową wersją technologii.

Składnik SQL Native Client (SNAC), które pakiety sterowników OLE DB i ODBC w pojedynczego pliku DLL jest przestarzała w przypadku aplikacji ODBC. Wersja programu SQL Server 2012 SNAC (SQLNCLI11. Biblioteka DLL) jest dostarczany z programem SQL Server 2016, ponieważ zależą od niej inne składniki programu SQL Server. Jednakże należy używać nowej aplikacji w języku C++, łączących się z programu SQL Server lub usługi Azure SQL Database za pomocą ODBC [najnowszych sterowników ODBC](/sql/connect/odbc/download-odbc-driver-for-sql-server). Aby uzyskać więcej informacji, zobacz [programu SQL Server Native klienta programowania](/sql/relational-databases/native-client/sql-server-native-client-programming)

Jeśli używasz C++/CLI, będzie można kontynuować używanie ADO.NET zawsze. Aby uzyskać więcej informacji, zobacz [ADO.NET za pomocą dostępu do danych (C++sposób niezamierzony)](../dotnet/data-access-using-adonet-cpp-cli.md), i [uzyskiwanie dostępu do danych w programie Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).

- Oprócz klas otoki ODBC MFC udostępnia klasy otoki obiektów dostępu do danych (DAO) do łączenia się z baz danych programu Access.  Jednak DAO jest przestarzała. Każdy kod, na podstawie CDaoDatabase lub CDaoRecordset powinny zostać uaktualnione.

Aby uzyskać więcej informacji o historii technologii dostępu do danych w programie Microsoft Windows, zobacz [Microsoft Data Access Components (Wikipedia)](https://en.wikipedia.org/wiki/Microsoft_Data_Access_Components).

## <a name="see-also"></a>Zobacz także

[Dostęp do danych](data-access-in-cpp.md)<br/>
[Microsoft Open Database Connectivity (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc)<br/>
