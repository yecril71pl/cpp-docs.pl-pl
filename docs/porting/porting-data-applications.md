---
title: Przenoszenie aplikacji danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/12/2017
ms.technology:
- devlang-cpp
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], data access applications
- databases [C++], MFC
- OLE DB [C++], data access technologies
- data [C++], data access technologies
- data access [C++], class libraries for databases
ms.assetid: 8d10c285-c13f-4e6e-a09e-5ee0f2666b44
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c20b9b6e8c1e96736485f302203156f627ef6794
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2018
ms.locfileid: "42464733"
---
# <a name="porting-data-applications"></a>Przenoszenie aplikacji danych
W ciągu lat Visual C++ udostępnia kilka metod do pracy z bazami danych. W 2011 r. Firma Microsoft ogłosiła, że jest ona wyrównywanie na ODBC jako preferowaną technologię do uzyskiwania dostępu do produktów SQL Server z kodu natywnego. ODBC jest standardem branżowym, a za jej pomocą uzyskasz uzyskania maksymalnej przenośności kodu na wielu platformach i źródeł danych. Większość produktów bazy danych SQL i wielu produktów NoSQL obsługują ODBC. Można użyć ODBC bezpośrednio, wywołując niskiego poziomu interfejsy API ODBC lub można użyć klasy otoki MFC ODBC lub innej biblioteki otoki języka C++. 

OLE DB to interfejs API niskiego poziomu, wysokiej wydajności na podstawie specyfikacji modelu COM i jest obsługiwane tylko dla Windows. Użyj OLE DB, jeśli program uzyskuje dostęp do [serwery połączone](/sql/relational-databases/linked-servers/linked-servers-database-engine). ATL zawiera szablony OLE DB, które ułatwiają tworzenie niestandardowych dostawców OLE DB i konsumentów. Najbardziej aktualną wersję OLE DB dostarczane w macierzystym 11 klienta SQL.  

Jeśli starszych aplikacji używa mechanizmu OLE DB lub wyższego poziomu interfejs ADO nawiązać połączenia z programem SQL Server, a nie uzyskujesz dostęp do połączonych serwerów, należy rozważyć Migrowanie do ODBC w niedalekiej przyszłości. Jeśli nie potrzebujesz między platformami lub najnowszych funkcji programu SQL Server, prawdopodobnie umożliwia dostawcy Microsoft OLE DB dla ODBC (MSDASQL).  MSDASQL umożliwia aplikacji, które są oparte na OLE DB i ADO (który jest używany wewnętrznie OLEDB) na dostęp do źródła danych za pośrednictwem sterownika ODBC. Podobnie jak w przypadku dowolnej warstwie tłumaczenia MSDASQL może wpłynąć na działanie bazy danych. Należy sprawdzić, czy wpływ jest signifant dla aplikacji. MSDASQL jest dostarczana z systemem operacyjnym Windows i Windows Server 2008 i Windows Vista z dodatkiem SP1 to Windows pierwszego wydania do uwzględnienia z 64-bitową wersją technologii.

Składnik SQL Native Client (SNAC), które pakiety sterowników OLE DB i ODBC w pojedynczego pliku DLL jest przestarzała w przypadku aplikacji ODBC. Wersja programu SQL Server 2012 SNAC (SQLNCLI11. Biblioteka DLL) jest dostarczany z programem SQL Server 2016, ponieważ zależą od niej inne składniki programu SQL Server. Jednakże należy używać nowej aplikacji w języku C++, łączących się z programu SQL Server lub usługi Azure SQL Database za pomocą ODBC [najnowszych sterowników ODBC](https://docs.microsoft.com/en-us/sql/connect/odbc/download-odbc-driver-for-sql-server). Aby uzyskać więcej informacji, zobacz [programu SQL Server Native klienta programowania](/sql/relational-databases/native-client/sql-server-native-client-programming)

Jeśli używasz języka C + +/ CLI, będzie można kontynuować używanie ADO.NET zawsze. Aby uzyskać więcej informacji, zobacz [ADO.NET za pomocą dostępu do danych (C + +/ CLI)](../dotnet/data-access-using-adonet-cpp-cli.md), i [uzyskiwanie dostępu do danych w programie Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).  
  
- Oprócz klas otoki ODBC MFC udostępnia klasy otoki dostępu obiekty DAO (Data) do łączenia się z baz danych programu Access.  Jednak DAO jest przestarzała. Na podstawie kodu `CDaoDatabase` lub `CDaoRecordset` powinny zostać uaktualnione. 

Aby uzyskać więcej informacji o historii technologii dostępu do danych w programie Microsoft Windows, zobacz [Microsoft Data Access Components (Wikipedia)](https://en.wikipedia.org/wiki/Microsoft_Data_Access_Components).  

## <a name="see-also"></a>Zobacz też  
 
[Dostęp do danych w programie Visual C++](../data/data-access-in-cpp.md)  
[Microsoft Open Database Connectivity (ODBC)](https://docs.microsoft.com/sql/odbc/microsoft-open-database-connectivity-odbc)  
[Mapy drogowej technologii dostępu do danych](https://msdn.microsoft.com/library/ms810810.aspx)  