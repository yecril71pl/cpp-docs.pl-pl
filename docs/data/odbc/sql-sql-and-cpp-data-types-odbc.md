---
title: 'SQL: typy danych SQL i C++ (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], SQL vs. C++
- SQL data types [C++]
- SQL [C++], vs. C++ data types
ms.assetid: 066e0070-d4da-435c-9c4b-f7cab3352c86
ms.openlocfilehash: 70796db02f8ff3fcfd67694fb596722664e8f904
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404258"
---
# <a name="sql-sql-and-c-data-types-odbc"></a>SQL: typy danych SQL i C++ (ODBC)

> [!NOTE]
> Te informacje dotyczą klas MFC ODBC. Jeśli pracujesz z klasami MFC DAO, zapoznaj się z tematem "porównanie usługi Microsoft Jet Database Engine SQL i ANSI SQL" w pomocy DAO.

Poniższa tabela mapuje typy danych SQL ANSI na typy danych języka C++. Rozszerza to informacje o języku C zawarte w dodatku D dokumentacji programu [ODBC Programmer's Reference](/sql/odbc/reference/odbc-programmer-s-reference) . Kreatorzy zarządzają najpopularniejszymi mapowaniami typów danych. Jeśli Kreator nie zostanie użyty, można użyć informacji o mapowaniu, aby ręcznie napisać kod wymiany pola.

### <a name="ansi-sql-data-types-mapped-to-c-data-types"></a>Typy danych SQL ANSI mapowane na typy danych języka C++

|ANSI — typ danych SQL|Typ danych języka C++|
|------------------------|---------------------|
|**DELIKATN**|`CString`|
|**DOKŁADNOŚCI**|`CString`jedno|
|**SMALLINT**|**int**|
|**CZASIE rzeczywistym**|**float**|
|**CAŁKOWITĄ**|**długi**|
|**FLOAT**|**Double**|
|**DOUBLE**|**Double**|
|**PRZYPADA**|`CString`jedno|
|**VARCHAR**|`CString`|
|**LONGVARCHAR**|`CLongBinary`, `CString` 2|
|**BIT**|**LOGICZNA**|
|**TINYINT**|**BYTE**|
|**BIGINT**|`CString`jedno|
|**BINARNY**|`CByteArray`|
|**LICZBY**|`CByteArray`|
|**LONGVARBINARY**|`CLongBinary`, `CByteArray` 3|
|**DNIU**|`CTime`, `CString`|
|**PIERWSZYM**|`CTime`, `CString`|
|**ZNACZNIK czasu**|`CTime`, `CString`|

1. **Liczba dziesiętna** ANSI i mapa **numeryczna** , z którą `CString` **SQL_C_CHAR** jest domyślnym typem transferu ODBC.

2. Dane znakowe przekraczające 255 znaków są obcinane domyślnie, gdy są mapowane na `CString` . Długość obcinania można zwiększyć, jawnie ustawiając argument *nMaxLength* `RFX_Text` .

3. Dane binarne poza 255 znaków są obcinane domyślnie po zmapowaniu do `CByteArray` . Długość obcinania można zwiększyć, jawnie ustawiając argument *nMaxLength* `RFX_Binary` .

Jeśli nie korzystasz z biblioteki kursorów ODBC, podczas próby zaktualizowania dwóch lub więcej długich pól o zmiennej długości przy użyciu sterownika Microsoft SQL Server ODBC i klas baz danych MFC ODBC mogą wystąpić problemy. Typy ODBC, **SQL_LONGVARCHAR** i **SQL_LONGVARBINARY**, mapują do typów SQL Server tekstowych i obrazów. `CDBException`Występuje, gdy aktualizujesz co najmniej dwa długie pola o zmiennej długości dla tego samego wywołania do `CRecordset::Update` . W związku z tym nie należy aktualizować jednocześnie wielu długich kolumn za pomocą `CRecordset::Update` . Można jednocześnie aktualizować wiele długich kolumn za pomocą interfejsu API ODBC `SQLPutData` . Możesz również użyć biblioteki kursora ODBC, ale nie jest to zalecane w przypadku sterowników, takich jak sterownik SQL Server, który obsługuje kursory i nie potrzebują biblioteki kursorów.

Jeśli używasz biblioteki kursorów ODBC z klasami baz danych MFC ODBC i Microsoft SQL Server sterownika ODBC, może wystąpić **potwierdzenie** wraz z `CDBException` wywołaniem wywołania `CRecordset::Update` do `CRecordset::Requery` . Zamiast tego należy wywołać metodę, `CRecordset::Close` a `CRecordset::Open` nie `CRecordset::Requery` . Innym rozwiązaniem jest użycie biblioteki kursora ODBC, ponieważ SQL Server i SQL Server sterownika ODBC zapewniają natywną obsługę kursorów natywnych, a Biblioteka kursorów ODBC nie jest wymagana.

## <a name="see-also"></a>Zobacz też

[SQL](../../data/odbc/sql.md)<br/>
[SQL: wykonywanie bezpośrednich wywołań SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
