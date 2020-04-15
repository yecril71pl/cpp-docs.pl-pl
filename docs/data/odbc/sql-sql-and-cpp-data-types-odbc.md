---
title: 'SQL: typy danych SQL i C++ (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], SQL vs. C++
- SQL data types [C++]
- SQL [C++], vs. C++ data types
ms.assetid: 066e0070-d4da-435c-9c4b-f7cab3352c86
ms.openlocfilehash: cffe44b832ac1eb28d368072b8f0e92ea9f57feb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374481"
---
# <a name="sql-sql-and-c-data-types-odbc"></a>SQL: typy danych SQL i C++ (ODBC)

> [!NOTE]
> Te informacje dotyczą klas Odbc MFC. Jeśli pracujesz z klasami DAO MFC, zobacz temat "Porównanie sql i SQL ansi programu MICROSOFT Jet Database Engine" w Pomocy DAO.

W poniższej tabeli mapuje typy danych SQL ANSI do typów danych języka C++. Zwiększa to informacje o języku C podane w dodatku D *odwołania programisty* *SDK ODBC* na dysku CD biblioteki MSDN. Kreatorzy zarządzają większością mapowania typów danych. Jeśli nie używasz kreatora, można użyć informacji mapowania, aby ułatwić ręczne pisanie kodu wymiany pól.

### <a name="ansi-sql-data-types-mapped-to-c-data-types"></a>Typy danych SQL ANSI mapowane na typy danych języka C++

|Typ danych SQL ANSI|Typ danych języka C++|
|------------------------|---------------------|
|**Char**|`CString`|
|**Dziesiętnych**|`CString`1|
|**Smallint**|**int**|
|**Prawdziwe**|**float**|
|**Liczba całkowita**|**long**|
|**Float**|**double**|
|**Podwójne**|**double**|
|**Liczbowe**|`CString`1|
|**Varchar**|`CString`|
|**LONGVARCHAR ( LONGVARCHAR )**|`CLongBinary`, `CString` 2|
|**Bitowych**|**Bool**|
|**Tinyint**|**Bajtów**|
|**Bigint**|`CString`1|
|**Binarnym**|`CByteArray`|
|**Varbinary**|`CByteArray`|
|**LONGVARBINARY**|`CLongBinary`, `CByteArray` 3|
|**Data**|`CTime`, `CString`|
|**CZAS**|`CTime`, `CString`|
|**Sygnatury czasowej**|`CTime`, `CString`|

1. ANSI **DECIMAL** i **NUMERIC** map, `CString` ponieważ **SQL_C_CHAR** jest domyślnym typem transferu ODBC.

2. Dane znaków powyżej 255 znaków są domyślnie `CString`obcinane podczas mapowania na . Długość obcinania można rozszerzyć, wyraźnie ustawiając argument *nMaxLength* . `RFX_Text`

3. Dane binarne przekraczające 255 znaków są `CByteArray`domyślnie obcinane podczas mapowania na . Długość obcinania można rozszerzyć, wyraźnie ustawiając argument *nMaxLength* . `RFX_Binary`

Jeśli nie używasz biblioteki kursora ODBC, może wystąpić problem podczas próby aktualizacji dwóch lub więcej długich pól o zmiennej długości przy użyciu sterownika ODBC programu Microsoft SQL Server i klas bazy danych OdBC MFC. Typy ODBC, **SQL_LONGVARCHAR** i **SQL_LONGVARBINARY,** mapują na tekst i obrazy typy programu SQL Server. A `CDBException` jest generowany, jeśli zaktualizujesz dwa lub `CRecordset::Update`więcej długich pól o zmiennej długości w tym samym wywołaniu . W związku z tym nie należy aktualizować wielu długich kolumn jednocześnie za pomocą programu `CRecordset::Update`. Można zaktualizować wiele długich kolumn jednocześnie `SQLPutData`z INTERFEJSEM API ODBC . Można również użyć biblioteki kursorów ODBC, ale nie jest to zalecane dla sterowników, takich jak sterownik programu SQL Server, które obsługują kursory i nie potrzebują biblioteki kursorów.

Jeśli używasz biblioteki kursora ODBC z klasami bazy danych OdBC MFC i sterownikiem ODBC programu `CRecordset::Update` Microsoft SQL `CRecordset::Requery`Server, może wystąpić **assert** wraz `CDBException` z, jeśli wywołanie następuje po wywołaniu . Zamiast tego `CRecordset::Close` zadzwoń, `CRecordset::Open` `CRecordset::Requery`a nie . Innym rozwiązaniem nie jest użycie biblioteki kursorów ODBC, ponieważ SQL Server i sterownik ODBC programu SQL Server zapewniają natywną obsługę kursorów natywnie, a biblioteka kursorów ODBC nie jest potrzebna.

## <a name="see-also"></a>Zobacz też

[SQL](../../data/odbc/sql.md)<br/>
[SQL: wykonywanie bezpośrednich wywołań SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
