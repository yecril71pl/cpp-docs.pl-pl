---
title: 'SQL: typy danych SQL i C++ (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], SQL vs. C++
- SQL data types [C++]
- SQL [C++], vs. C++ data types
ms.assetid: 066e0070-d4da-435c-9c4b-f7cab3352c86
ms.openlocfilehash: 1c1ce908b5c8d345906d49adc79e322225ed49f5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212618"
---
# <a name="sql-sql-and-c-data-types-odbc"></a>SQL: typy danych SQL i C++ (ODBC)

> [!NOTE]
>  Te informacje dotyczą klas MFC ODBC. Jeśli pracujesz z klasami MFC DAO, zapoznaj się z tematem "porównanie usługi Microsoft Jet Database Engine SQL i ANSI SQL" w pomocy DAO.

Poniższa tabela mapuje typy danych SQL ANSI C++ na typy danych. Rozszerza to informacje o języku C zawarte w dodatku D odwołania do *zestawu ODBC SDK* *programisty* na dysku CD biblioteki MSDN. Kreatorzy zarządzają najpopularniejszymi mapowaniami typów danych. Jeśli Kreator nie zostanie użyty, można użyć informacji o mapowaniu, aby ręcznie napisać kod wymiany pola.

### <a name="ansi-sql-data-types-mapped-to-c-data-types"></a>Typy danych SQL ANSI mapowane na C++ typy danych

|ANSI — typ danych SQL|C++Typ danych|
|------------------------|---------------------|
|**DELIKATN**|`CString`|
|**DOKŁADNOŚCI**|`CString` 1|
|**SMALLINT**|**int**|
|**CZASIE rzeczywistym**|**float**|
|**CAŁKOWITĄ**|**long**|
|**FLOAT**|**double**|
|**DOUBLE**|**double**|
|**PRZYPADA**|`CString` 1|
|**VARCHAR**|`CString`|
|**LONGVARCHAR**|`CLongBinary`, `CString` 2|
|**BIT**|**LOGICZNA**|
|**TINYINT**|**BAJC**|
|**BIGINT**|`CString` 1|
|**BINARNY**|`CByteArray`|
|**LICZBY**|`CByteArray`|
|**LONGVARBINARY**|`CLongBinary`, `CByteArray` 3|
|**DATE**|`CTime`, `CString`|
|**CZAS**|`CTime`, `CString`|
|**ZNACZNIK czasu**|`CTime`, `CString`|

1. **Liczba dziesiętna** i mapa **numeryczna** ANSI do `CString`, ponieważ **SQL_C_CHAR** jest domyślnym typem transferu ODBC.

2. Dane znakowe przekraczające 255 znaków są domyślnie obcinane po zmapowaniu na `CString`. Długość obcinania można zwiększyć przez jawne ustawienie argumentu *nMaxLength* `RFX_Text`.

3. Dane binarne przekraczające 255 znaków są domyślnie obcinane po zmapowaniu na `CByteArray`. Długość obcinania można zwiększyć przez jawne ustawienie argumentu *nMaxLength* `RFX_Binary`.

Jeśli nie korzystasz z biblioteki kursorów ODBC, podczas próby zaktualizowania dwóch lub więcej długich pól o zmiennej długości przy użyciu sterownika Microsoft SQL Server ODBC i klas baz danych MFC ODBC mogą wystąpić problemy. Typy ODBC, **SQL_LONGVARCHAR** i **SQL_LONGVARBINARY**, mapują do typów SQL Server tekstowych i obrazów. Zostanie zgłoszony `CDBException`, jeśli do `CRecordset::Update`zostanie zaktualizowanych co najmniej dwóch pól o zmiennej długości. W związku z tym nie należy aktualizować wielu długich kolumn jednocześnie przy użyciu `CRecordset::Update`. Można jednocześnie aktualizować wiele długich kolumn za pomocą interfejsu API ODBC `SQLPutData`. Możesz również użyć biblioteki kursora ODBC, ale nie jest to zalecane w przypadku sterowników, takich jak sterownik SQL Server, który obsługuje kursory i nie potrzebują biblioteki kursorów.

Jeśli używasz biblioteki kursorów ODBC z klasami baz danych MFC ODBC i Microsoft SQL Server sterownika ODBC, może wystąpić **potwierdzenie** wraz z `CDBException`, jeśli wywołanie `CRecordset::Update` następuje po wywołaniu `CRecordset::Requery`. Zamiast tego wywołaj `CRecordset::Close` i `CRecordset::Open`, a nie `CRecordset::Requery`. Innym rozwiązaniem jest użycie biblioteki kursora ODBC, ponieważ SQL Server i SQL Server sterownika ODBC zapewniają natywną obsługę kursorów natywnych, a Biblioteka kursorów ODBC nie jest wymagana.

## <a name="see-also"></a>Zobacz też

[SQL](../../data/odbc/sql.md)<br/>
[SQL: wykonywanie bezpośrednich wywołań SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
