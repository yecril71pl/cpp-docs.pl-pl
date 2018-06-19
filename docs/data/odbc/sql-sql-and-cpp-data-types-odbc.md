---
title: 'SQL: SQL i typy danych języka C++ (ODBC) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data types [C++], SQL vs. C++
- SQL data types [C++]
- SQL [C++], vs. C++ data types
ms.assetid: 066e0070-d4da-435c-9c4b-f7cab3352c86
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6a137c4f648f518420d06f5cbd98ea189a030aee
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095411"
---
# <a name="sql-sql-and-c-data-types-odbc"></a>SQL: typy danych SQL i C++ (ODBC)
> [!NOTE]
>  Te informacje dotyczą klasach MFC ODBC. Jeśli pracujesz z klas MFC DAO, zobacz temat "Porównanie z bazy danych aparatu SQL i ANSI SQL programu Microsoft Jet" w pomocy DAO.  
  
 Poniższa tabela mapowania typów danych ANSI SQL do typy danych języka C++. Rozszerza dane języka C z dodatkiem D *ODBC SDK* *Podręcznik programisty* na dysku CD biblioteki MSDN. Kreatorzy Zarządzanie większości mapowanie typu danych dla Ciebie. Jeśli nie używasz kreatora, można użyć informacje dotyczące mapowania ułatwia pisanie kodu exchange pola ręcznie.  
  
### <a name="ansi-sql-data-types-mapped-to-c-data-types"></a>Typy danych języka SQL ANSI zamapowane na typy danych języka C++  
  
|Typ danych ANSI SQL|Typ danych języka C++|  
|------------------------|---------------------|  
|**CHAR**|`CString`|  
|**DECIMAL**|`CString` 1|  
|**SMALLINT**|`int`|  
|`REAL`|**float**|  
|**LICZBA CAŁKOWITA**|**long**|  
|**FLOAT**|**double**|  
|**O PODWÓJNEJ PRECYZJI**|**double**|  
|**NUMERYCZNE**|`CString` 1|  
|**VARCHAR**|`CString`|  
|**LONGVARCHAR**|`CLongBinary`, `CString` 2|  
|**BITOWE**|**BOOL**|  
|**TINYINT**|**BAJTÓW**|  
|**BIGINT**|`CString` 1|  
|**BINARNE**|`CByteArray`|  
|**VARBINARY**|`CByteArray`|  
|**LONGVARBINARY**|`CLongBinary`, `CByteArray` 3|  
|**DATA**|`CTime`, `CString`|  
|**CZAS**|**Ctime —, cstring —**|  
|**ZNACZNIK CZASU**|**Ctime —, cstring —**|  
  
 1. ANSI **DZIESIĘTNĄ** i **liczbowych** mapowania `CString` ponieważ **SQL_C_CHAR** jest to domyślny typ transferu ODBC.  
  
 2. Domyślnie, jeśli są mapowane na zostały obcięte dane znaków innych niż 255 znaków `CString`. Długość obcięcie można rozszerzyć, jawnie ustawiając `nMaxLength` argument `RFX_Text`.  
  
 3. Dane binarne ponad 255 znaków zostały obcięte domyślnie, jeśli są mapowane na `CByteArray`. Długość obcięcie można rozszerzyć, jawnie ustawiając `nMaxLength` argument `RFX_Binary`.  
  
 Jeśli nie używasz z biblioteki kursorów ODBC, może wystąpić problem podczas próby zaktualizowania dwa lub więcej pól długo o zmiennej długości, za pomocą sterownika ODBC programu Microsoft SQL Server i klasy baz danych MFC ODBC. Typy ODBC **SQL_LONGVARCHAR** i **SQL_LONGVARBINARY**, mapy Text i obrazów typów programu SQL Server. A `CDBException` jest zgłaszany w przypadku aktualizacji co najmniej dwoma polami długo o zmiennej długości, w tym samym wywołaniu `CRecordset::Update`. W związku z tym nie zaktualizować wiele kolumn długi równocześnie z `CRecordset::Update`. Zaktualizuj wiele kolumn długi jednocześnie przy użyciu interfejsu API ODBC **SQLPutData**. Można również korzystanie z biblioteki kursorów ODBC, ale nie jest to zalecane dla sterowników, takie jak sterownik programu SQL Server obsługuje kursorów, które nie są z biblioteki kursorów.  
  
 Korzystając z biblioteki kursorów ODBC z klasami baz danych MFC ODBC i sterownik Microsoft ODBC dla programu SQL Server **ASSERT** może wystąpić wraz z `CDBException` Jeśli wywołanie `CRecordset::Update` następuje po wywołaniu `CRecordset::Requery`. Zamiast tego wywołać `CRecordset::Close` i `CRecordset::Open` zamiast `CRecordset::Requery`. Innym rozwiązaniem jest nie należy używać z biblioteki kursorów ODBC, ponieważ serwer SQL i sterownik ODBC programu SQL Server zapewniają natywną obsługę kursory natywnie i Biblioteka kursorów ODBC nie jest wymagana.  
  
## <a name="see-also"></a>Zobacz też  
 [SQL](../../data/odbc/sql.md)   
 [SQL: wykonywanie bezpośrednich wywołań SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)