---
title: Eksportowanie danych aplikacji | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 05/12/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC [C++], data access applications
- databases [C++], MFC
- OLE DB [C++], data access technologies
- data [C++], data access technologies
- data access [C++], class libraries for databases
ms.assetid: 8d10c285-c13f-4e6e-a09e-5ee0f2666b44
caps.latest.revision: "0"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0409df12df704e52e48f68b193d914d9241cf812
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="porting-data-applications"></a>Eksportowanie danych aplikacji
Całościowo Visual C++ oferuje wiele możliwości korzystania z bazy danych. 2011 firma Microsoft poinformowała, że jest ona wyrównywanie na ODBC jako preferowaną technologią do uzyskiwania dostępu do programu SQL Server produkty z kodu macierzystego. ODBC jest standardem branżowym i za jego pomocą uzyskać maksymalną przenośność kodu przez wiele platform i źródeł danych. Większość produktów bazy danych SQL i wiele produktów NoSQL obsługuje ODBC. Można użyć ODBC bezpośrednio przez wywoływanie funkcji interfejsu API ODBC niskiego poziomu, lub skorzystać z MFC ODBC — klasy otoki lub biblioteki otoki C++ innych firm. 

OLE DB to interfejs API niskiego poziomu, wysokiej wydajności na podstawie specyfikacji modelu COM i jest obsługiwany tylko w systemie Windows. Użyj OLE DB, jeśli podczas uzyskiwania dostępu do programu [połączonych serwerów](/sql/relational-databases/linked-servers/linked-servers-database-engine). ATL zawiera szablony OLE DB, które ułatwiają tworzenie niestandardowych dostawców OLE DB i konsumentów. Wysłane najnowszej wersji bazy danych OLE DB programu SQL Native 11 klienta.  

Jeśli starszych aplikacji OLE DB lub wyższego poziomu interfejs ADO do połączenia z serwerem SQL, a nie uzyskują dostęp do połączonych serwerów, należy rozważyć Migrowanie do ODBC w najbliższej przyszłości. Jeśli nie wymagają przenośność i platform lub najnowsze funkcje programu SQL Server, prawdopodobnie można dostawcy Microsoft OLE DB dla ODBC (MSDASQL).  MSDASQL umożliwia aplikacjom utworzonym w OLE DB i ADO (używający OLEDB wewnętrznie) dostęp do źródła danych za pośrednictwem sterownika ODBC. Podobnie jak w przypadku dowolnego warstwa tłumaczenia MSDASQL może wpłynąć na działanie bazy danych. Należy przetestować, aby ustalić, czy wpływ signifant aplikacji. MSDASQL jest dostarczana z systemem operacyjnym Windows i Windows Server 2008 i Windows Vista z dodatkiem SP1 to pierwszy Windows zwalnia uwzględnienie 64-bitowej wersji technologii.

Składnik programu SQL Native Client (SNAC), które pakiety sterowników OLE DB i ODBC w pojedynczego pliku DLL jest przestarzała w przypadku aplikacji ODBC. Wersja programu SQL Server 2012 SNAC (SQLNCLI11. Biblioteki DLL) jest dostarczany z programu SQL Server 2016, ponieważ zależą od niej inne składniki programu SQL Server. Jednak używać nowej aplikacji C++ łączących się z serwerem SQL lub bazy danych SQL Azure za pośrednictwem ODBC [najnowszych sterowników ODBC](https://docs.microsoft.com/en-us/sql/connect/odbc/download-odbc-driver-for-sql-server). Aby uzyskać więcej informacji, zobacz [programu SQL Server Native klienta programowania](/sql/relational-databases/native-client/sql-server-native-client-programming)

Jeśli używasz C + +/ CLI, można nadal używać ADO.NET jako zawsze. Aby uzyskać więcej informacji, zobacz [danych dostęp za pomocą ADO.NET (C + +/ CLI)](../dotnet/data-access-using-adonet-cpp-cli.md), i [uzyskiwanie dostępu do danych w programie Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).  
  
-   Oprócz ODBC — klasy otoki MFC zawiera klasy otoki dostęp obiekty DAO (Data) w celu nawiązania baz danych programu Access.  Jednak DAO jest przestarzała. Każdy kod na podstawie CDaoDatabase lub cdaorecordset — powinny zostać uaktualnione. 

Aby uzyskać więcej informacji o historii technologie dostępu do danych w systemie Microsoft Windows, temacie [Microsoft Data Access Components (Wikipedia)](https://en.wikipedia.org/wiki/Microsoft_Data_Access_Components).  

## <a name="see-also"></a>Zobacz też  
 [Dostęp do danych w programie Visual C++](../data/data-access-in-cpp.md)  
 [Microsoft Open łączność z bazą danych (ODBC)](https://docs.microsoft.com/sql/odbc/microsoft-open-database-connectivity-odbc)  
 [Mapy drogowej technologii dostępu do danych](https://msdn.microsoft.com/en-us/library/ms810810.aspx)  