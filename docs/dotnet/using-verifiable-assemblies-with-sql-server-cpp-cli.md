---
title: "Używanie zestawów weryfikowalnych z programem SQL Server (C + +/ CLI) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: verifiable assemblies [C++], with SQL Server
ms.assetid: 5248a60d-aa88-4ff3-b30a-b791c3ea2de9
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8c102d06e360c97f5c86e613ece869d4d38c4fc9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="using-verifiable-assemblies-with-sql-server-ccli"></a>Używanie zestawów weryfikowalnych z programem SQL Server (C++/CLI)
Rozszerzone procedury składowane dostarczana w bibliotek dołączanych dynamicznie (dll), zapewnia możliwości rozszerzania funkcji programu SQL Server za pośrednictwem funkcji utworzonych w języku Visual C++. Rozszerzone procedury składowane są zaimplementowane jako funkcjami wewnątrz biblioteki dll. Oprócz funkcji, można również zdefiniować rozszerzonych procedur składowanych [typy danych zdefiniowane przez użytkownika](../cpp/classes-and-structs-cpp.md) i [funkcje agregujące](http://msdn.microsoft.com/en-us/de255454-f45e-4281-81f9-bc61893ac5da) (np. Suma lub AVG).  
  
 Gdy klient wykonuje rozszerzoną procedurę składowaną, wyszukiwanie programu SQL Server dla biblioteki DLL skojarzone z rozszerzoną procedurę składowaną i ładuje bibliotekę DLL. SQL Server wywołuje żądanego rozszerzoną procedurę składowaną i wykonuje go w kontekście zabezpieczeń określony. Rozszerzonej procedury składowanej, a następnie przekazuje wynik ustawia i zwraca parametry do serwera.  
  
 [!INCLUDE[sqprsqlong](../dotnet/includes/sqprsqlong_md.md)]udostępnia rozszerzenia do języka Transact-SQL (T-SQL), aby umożliwić zainstalowanie zestawy podlegające weryfikacji do programu SQL Server. Zestaw uprawnień programu SQL Server Określa kontekst zabezpieczeń z następujących poziomów zabezpieczeń:  
  
-   Trybie nieograniczonym: uruchamianie kodu na własne ryzyko; kod nie musi być sprawdzalnie bezpieczny.  
  
-   Tryb awaryjny: uruchamianie sprawdzalnie umożliwić kodu; skompilowane z/CLR: Safe.  
  
 Tryb awaryjny wymaga wykonanego zestawy sprawdzalnie należy umożliwić.  
  
 Aby utworzyć i załadować możliwe do zweryfikowania zestawu do programu SQL Server, użyj polecenia języka Transact-SQL, Utwórz zestaw i DROP ASSEMBLY w następujący sposób:  
  
```  
CREATE ASSEMBLY <assemblyName> FROM <'Assembly UNC Path'> WITH   
  PERMISSION_SET <permissions>  
DROP ASSEMBLY <assemblyName>  
```  
  
 Polecenie PERMISSION_SET Określa kontekst zabezpieczeń i może mieć wartości bez ograniczeń, bezpieczne lub ROZSZERZONE.  
  
 Ponadto służy polecenie CREATE FUNCTION powiązać nazwy metod w klasie:  
  
```  
CREATE FUNCTION <FunctionName>(<FunctionParams>)  
RETURNS returnType  
[EXTERNAL NAME <AssemblyName>:<ClassName>::<StaticMethodName>]  
```  
  
## <a name="example"></a>Przykład  
 Poniższy skrypt SQL (na przykład o nazwie "MyScript.sql") ładuje zestaw do programu SQL Server i udostępnia metody klasy:  
  
```  
-- Create assembly without external access  
drop assembly stockNoEA  
go  
create assembly stockNoEA  
from   
'c:\stockNoEA.dll'  
with permission_set safe  
  
-- Create function on assembly with no external access  
drop function GetQuoteNoEA  
go  
create function GetQuoteNoEA(@sym nvarchar(10))  
returns real  
external name stockNoEA:StockQuotes::GetQuote  
go  
  
-- To call the function  
select dbo.GetQuoteNoEA('MSFT')  
go  
```  
  
 Skrypty SQL mogą być wykonywane interakcyjnego w analizatorze kwerend SQL lub w wierszu polecenia przy użyciu narzędzia sqlcmd.exe. Następujące polecenie w wierszu łączy się MójSerwer, używa domyślnej bazy danych używa zaufanego połączenia, danych wejściowych MyScript.sql i wyprowadza MyResult.txt.  
  
```  
sqlcmd -S MyServer -E -i myScript.sql -o myResult.txt  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Migracja do/CLR: safe (C + +/ CLI)](../dotnet/how-to-migrate-to-clr-safe-cpp-cli.md)   
 [Klasy i struktury](../cpp/classes-and-structs-cpp.md)