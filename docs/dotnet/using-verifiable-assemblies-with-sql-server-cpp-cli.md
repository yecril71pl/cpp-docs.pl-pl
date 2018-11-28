---
title: Używanie zestawów weryfikowalnych z programem SQL Server (C++/CLI)
ms.date: 10/17/2018
helpviewer_keywords:
- verifiable assemblies [C++], with SQL Server
ms.assetid: 5248a60d-aa88-4ff3-b30a-b791c3ea2de9
ms.openlocfilehash: a977aa81a598e1698dfbc1c5679b85378b7ba6fc
ms.sourcegitcommit: d04dfe95801bafcbd5371e40e626fe5c678343b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389932"
---
# <a name="using-verifiable-assemblies-with-sql-server-ccli"></a>Używanie zestawów weryfikowalnych z programem SQL Server (C++/CLI)

Rozszerzone procedury składowane spakowany jako bibliotek dołączanych dynamicznie (dll), umożliwiają do rozszerzania funkcji programu SQL Server za pomocą funkcji przygotowane w programie Visual C++. Rozszerzone procedury składowane są implementowane jako funkcjami wewnątrz biblioteki dll. Oprócz funkcji, rozszerzone procedury składowane można również zdefiniować [typy zdefiniowane przez użytkownika](../cpp/classes-and-structs-cpp.md) i agregowanie funkcji (np. Suma lub średnia).

Gdy klient wykonuje procedurę przechowywaną, wyszukiwanie programu SQL Server dla biblioteki DLL skojarzone z rozszerzoną procedurę składowaną i ładuje bibliotekę DLL. Program SQL Server wywołuje żądanego rozszerzoną procedurę składowaną i wykonuje go w kontekście zabezpieczeń określonym. Rozszerzonej procedury składowanej, a następnie wyników przebiegów ustawia i zwraca parametry do serwera.

Program SQL Server udostępnia rozszerzenia do języka Transact-SQL (T-SQL), aby umożliwić zainstalowanie zestawy podlegające weryfikacji do programu SQL Server. Zestaw uprawnień programu SQL Server Określa kontekst zabezpieczeń, z następującymi poziomami zabezpieczeń:

- Tryb bez ograniczeń: uruchamianie kodu na własne ryzyko; kod nie musi być sprawdzalnie bezpieczny.

- Tryb awaryjny: Uruchom weryfikowalny pod kątem zapewnienia kodu. skompilowane z/CLR: Safe.

> [!IMPORTANT]
> Przestarzałe w programie Visual Studio 2015 i Visual Studio 2017 nie obsługuje **/CLR: pure** i **/CLR: Safe** tworzenie weryfikowalnych projektów. Jeśli potrzebujesz weryfikowalny kod, zalecamy Przetłumacz swój kod C#.

Aby utworzyć i załadować zestawów weryfikowalnych do programu SQL Server, użyj polecenia języka Transact-SQL, instrukcja CREATE ASSEMBLY i wykonanie polecenia DROP ASSEMBLY w następujący sposób:

```sql
CREATE ASSEMBLY <assemblyName> FROM <'Assembly UNC Path'> WITH
  PERMISSION_SET <permissions>
DROP ASSEMBLY <assemblyName>
```

Polecenie PERMISSION_SET Określa kontekst zabezpieczeń i może mieć wartości bez ograniczeń, bezpieczne lub ROZSZERZONE.

Ponadto można użyć polecenia CREATE FUNCTION powiązać nazwy metod w klasie:

```sql
CREATE FUNCTION <FunctionName>(<FunctionParams>)
RETURNS returnType
[EXTERNAL NAME <AssemblyName>:<ClassName>::<StaticMethodName>]
```

## <a name="example"></a>Przykład

Poniższy skrypt SQL (na przykład o nazwie "MyScript.sql"), ładuje zestaw do programu SQL Server i udostępnia metodę klasy:

```sql
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

```cmd
sqlcmd -S MyServer -E -i myScript.sql -o myResult.txt
```

## <a name="see-also"></a>Zobacz też

[Klasy i struktury](../cpp/classes-and-structs-cpp.md)
