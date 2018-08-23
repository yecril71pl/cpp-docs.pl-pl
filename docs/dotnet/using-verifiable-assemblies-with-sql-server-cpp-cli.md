---
title: Używanie zestawów weryfikowalnych z programem SQL Server (C + +/ CLI) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- verifiable assemblies [C++], with SQL Server
ms.assetid: 5248a60d-aa88-4ff3-b30a-b791c3ea2de9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b35675ba0081ec4ea7a1c9559f9a8fb71347cd54
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42583822"
---
# <a name="using-verifiable-assemblies-with-sql-server-ccli"></a>Używanie zestawów weryfikowalnych z programem SQL Server (C++/CLI)
Rozszerzone procedury składowane spakowany jako bibliotek dołączanych dynamicznie (dll), umożliwiają do rozszerzania funkcji programu SQL Server za pomocą funkcji przygotowane w programie Visual C++. Rozszerzone procedury składowane są implementowane jako funkcjami wewnątrz biblioteki dll. Oprócz funkcji, rozszerzone procedury składowane można również zdefiniować [typy zdefiniowane przez użytkownika](../cpp/classes-and-structs-cpp.md) i [funkcje](http://msdn.microsoft.com/en-us/de255454-f45e-4281-81f9-bc61893ac5da) (na przykład Suma lub średnia).  
  
 Gdy klient wykonuje procedurę przechowywaną, wyszukiwanie programu SQL Server dla biblioteki DLL skojarzone z rozszerzoną procedurę składowaną i ładuje bibliotekę DLL. Program SQL Server wywołuje żądanego rozszerzoną procedurę składowaną i wykonuje go w kontekście zabezpieczeń określonym. Rozszerzonej procedury składowanej, a następnie wyników przebiegów ustawia i zwraca parametry do serwera.  
  
 Program SQL Server udostępnia rozszerzenia do języka Transact-SQL (T-SQL), aby umożliwić zainstalowanie zestawy podlegające weryfikacji do programu SQL Server. Zestaw uprawnień programu SQL Server Określa kontekst zabezpieczeń, z następującymi poziomami zabezpieczeń:  
  
-   Tryb bez ograniczeń: uruchamianie kodu na własne ryzyko; kod nie musi być sprawdzalnie bezpieczny.  
  
-   Tryb awaryjny: Uruchom weryfikowalny pod kątem zapewnienia kodu. skompilowane z/CLR: Safe.  
  
 Tryb awaryjny wymaga wykonanych zestawów, które mają być weryfikowalny pod kątem zapewnienia.  
  
 Aby utworzyć i załadować zestawów weryfikowalnych do programu SQL Server, użyj polecenia języka Transact-SQL, instrukcja CREATE ASSEMBLY i wykonanie polecenia DROP ASSEMBLY w następujący sposób:  
  
```  
CREATE ASSEMBLY <assemblyName> FROM <'Assembly UNC Path'> WITH   
  PERMISSION_SET <permissions>  
DROP ASSEMBLY <assemblyName>  
```  
  
 Polecenie PERMISSION_SET Określa kontekst zabezpieczeń i może mieć wartości bez ograniczeń, bezpieczne lub ROZSZERZONE.  
  
 Ponadto można użyć polecenia CREATE FUNCTION powiązać nazwy metod w klasie:  
  
```  
CREATE FUNCTION <FunctionName>(<FunctionParams>)  
RETURNS returnType  
[EXTERNAL NAME <AssemblyName>:<ClassName>::<StaticMethodName>]  
```  
  
## <a name="example"></a>Przykład  
 Poniższy skrypt SQL (na przykład o nazwie "MyScript.sql"), ładuje zestaw do programu SQL Server i udostępnia metodę klasy:  
  
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
  
 Skrypty SQL mogą być wykonywane interaktywnie w analizatorze kwerend SQL lub w wierszu polecenia przy użyciu narzędzia sqlcmd.exe. Następujące polecenie w wierszu nawiązanie połączenia z MójSerwer, używa domyślnej bazy danych, używa zaufane połączenie, danych wejściowych MyScript.sql i generuje MyResult.txt.  
  
```  
sqlcmd -S MyServer -E -i myScript.sql -o myResult.txt  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Migracja do/CLR: safe (C + +/ CLI)](../dotnet/how-to-migrate-to-clr-safe-cpp-cli.md)   
 [Klasy i struktury](../cpp/classes-and-structs-cpp.md)