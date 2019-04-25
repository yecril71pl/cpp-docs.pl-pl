---
title: 'SQL: Program SQL oraz typów danych języka C++ (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], SQL vs. C++
- SQL data types [C++]
- SQL [C++], vs. C++ data types
ms.assetid: 066e0070-d4da-435c-9c4b-f7cab3352c86
ms.openlocfilehash: 3efa36342b7d16968113acd818a7a1386e4cefcc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62329891"
---
# <a name="sql-sql-and-c-data-types-odbc"></a>SQL: Program SQL oraz typów danych języka C++ (ODBC)

> [!NOTE]
>  Te informacje dotyczą klas MFC ODBC. Pracy przy użyciu klas MFC DAO, zobacz temat "Porównanie programu Microsoft Jet bazy danych aparatu SQL i ANSI SQL" w Pomocy programu DAO.

Poniższa tabela zawiera mapowanie typów danych ANSI SQL do typów danych języka C++. Rozszerza informacje o języku C, które zostały podane w dodatku D *ODBC SDK* *odwołania programisty* na dysku CD z biblioteki MSDN. Kreatorzy Zarządzanie większość mapowanie typu danych dla Ciebie. Jeśli nie używasz kreatora, można użyć informacje dotyczące mapowania ułatwiają ręcznie napisać kod programem exchange.

### <a name="ansi-sql-data-types-mapped-to-c-data-types"></a>Typy danych SQL ANSI mapowane na typy danych języka C++

|Typ danych ANSI SQL|Typów danych języka C++|
|------------------------|---------------------|
|**CHAR**|`CString`|
|**DECIMAL**|`CString` 1|
|**SMALLINT**|**int**|
|**RZECZYWISTE**|**float**|
|**INTEGER**|**long**|
|**FLOAT**|**double**|
|**PODWÓJNE**|**double**|
|**NUMERYCZNE**|`CString` 1|
|**VARCHAR**|`CString`|
|**LONGVARCHAR**|`CLongBinary`, `CString` 2|
|**BIT**|**BOOL**|
|**TINYINT**|**BAJTÓW**|
|**BIGINT**|`CString` 1|
|**BINARNY**|`CByteArray`|
|**VARBINARY**|`CByteArray`|
|**LONGVARBINARY**|`CLongBinary`, `CByteArray` 3|
|**DATA**|`CTime`, `CString`|
|**CZAS**|`CTime`, `CString`|
|**ZNACZNIK CZASU:**|`CTime`, `CString`|

1. ANSI **dziesiętna** i **liczbowych** mapowania `CString` ponieważ **SQL_C_CHAR** jest domyślnym typem transferu ODBC.

2. Dane znak poza 255 znaków są obcinane domyślnie, gdy mapowane na `CString`. Wydłużyć obcięcie poprzez jawne ustawienie *nMaxLength* argument `RFX_Text`.

3. Domyślnie, gdy mapowane na zostały obcięte dane binarne przekracza 255 znaków `CByteArray`. Wydłużyć obcięcie poprzez jawne ustawienie *nMaxLength* argument `RFX_Binary`.

Jeśli nie jest używany z biblioteki kursorów ODBC, może wystąpić problem podczas próby zaktualizowania dwa lub więcej pól długo o zmiennej długości, za pomocą sterownika Microsoft ODBC dla programu SQL Server i klasy baz danych MFC ODBC. Typy ODBC **SQL_LONGVARCHAR** i **SQL_LONGVARBINARY**, mapy do tekstu i obrazów typów programu SQL Server. A `CDBException` jest generowany, jeśli zaktualizujesz dwa lub więcej pól długo o zmiennej długości, w tym samym wywołaniu `CRecordset::Update`. W związku z tym, nie są uaktualniane wiele kolumn długich równocześnie z `CRecordset::Update`. Aktualizowanie wielu kolumn długich jednocześnie przy użyciu interfejsu API ODBC `SQLPutData`. Można również korzystać z biblioteki kursorów ODBC, ale nie jest to zalecane dla sterowników, takie jak sterownik programu SQL Server obsługuje kursorów, które nie są z biblioteki kursorów.

Jeśli korzystasz z biblioteki kursorów ODBC z klas baz danych MFC ODBC i sterownik Microsoft ODBC dla programu SQL Server **ASERCJA** mogą wystąpić wraz z `CDBException` Jeśli wywołanie `CRecordset::Update` następuje po wywołaniu `CRecordset::Requery`. Zamiast tego należy wywołać `CRecordset::Close` i `CRecordset::Open` zamiast `CRecordset::Requery`. Innym rozwiązaniem jest, aby nie korzystała z biblioteki kursorów ODBC, ponieważ serwer SQL i sterownik SQL Server ODBC zapewniają natywną obsługę kursory natywnie i z biblioteki kursorów ODBC nie jest potrzebna.

## <a name="see-also"></a>Zobacz także

[SQL](../../data/odbc/sql.md)<br/>
[SQL: Wykonywanie bezpośrednich wywołań SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)