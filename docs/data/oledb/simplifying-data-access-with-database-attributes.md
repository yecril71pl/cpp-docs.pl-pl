---
title: Upraszczanie dostępu do danych za pomocą atrybutów bazy danych
ms.date: 10/19/2018
f1_keywords:
- vc-attr.db_param
- vc-attr.db_column
- vc-attr.db_accessor
- vc-attr.db_command
- vc-attr.db_table
- vc-attr.db_source
helpviewer_keywords:
- attributes [C++], database
- attributes [C++], data access
- databases [C++], attributes
- data [C++], simplifying access
- data access [C++], database attributes
- database attributes [C++]
- OLE DB consumers [C++], database attributes
- attributes [C++], OLE DB consumer
ms.assetid: 560d2456-e307-4cb7-ba7b-4d0ed674697f
ms.openlocfilehash: 83519ffff7dd1f1b5f8a635f094932a1f9728193
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59031053"
---
# <a name="simplifying-data-access-with-database-attributes"></a>Upraszczanie dostępu do danych za pomocą atrybutów bazy danych

W tym temacie przedstawiono użycie atrybutów bazy danych, aby uprościć operacji bazy danych.

Podstawowy sposób uzyskiwać dostęp do informacji z bazy danych ma utworzyć klasę polecenie (lub tabeli) i klasę rekordu użytkownika dla określonej tabeli w bazie danych. Atrybuty bazy danych, Uprość niektóre deklaracje szablonu, które wcześniej trzeba było zrobić.

Aby zademonstrować użycie atrybutów bazy danych, w poniższych sekcjach opisano dwa równoważne tabeli i deklaracji klasy rekordów użytkowników: pierwszy używa atrybutów, a drugi używa szablony OLE DB. Taki kod deklaracji zwykle jest umieszczany w pliku nagłówka o nazwie dla obiektu tabeli lub polecenia, na przykład Authors.h.

Przez porównanie dwóch plików, można zobaczyć, jak łatwiej jest używać atrybutów. Wśród różnice są:

- Przy użyciu atrybutów, należy zadeklarować jednej klasy: `CAuthors`, podczas gdy za pomocą szablonów należy zadeklarować dwa: `CAuthorsNoAttrAccessor` i `CAuthorsNoAttr`.

- `db_source` Wywołania w wersji opartego na atrybutach jest odpowiednikiem `OpenDataSource()` wywołania w deklaracji szablonu.

- `db_table` Wywołania w wersji opartego na atrybutach jest równoważna następującej deklaracji szablonu:

    ```cpp
    class CAuthorsNoAttr : public CTable<CAccessor<CAuthorsNoAttrAccessor>>
    ```

- `db_column` Wywołań w wersji opartego na atrybutach są równoważne do mapy kolumny (zobacz `BEGIN_COLUMN_MAP ... END_COLUMN_MAP`) w deklaracji szablonu.

Atrybuty wstrzyknąć deklarację klasy rekordu użytkownika za Ciebie. Klasa rekord użytkownika jest równa `CAuthorsNoAttrAccessor` w deklaracji szablonu. Jeśli klasa tabeli `CAuthors`, nosi nazwę klasy rekordu użytkownika wprowadzony `CAuthorsAccessor`, i może wyświetlać tylko jego deklaracji w wprowadzonego kodu. Aby uzyskać więcej informacji, zobacz "Klasy rekordów użytkowników Attribute-Injected" w [rekordów użytkowników](../../data/oledb/user-records.md).

Zarówno w atrybutami i kodu opartego na szablonie, należy ustawić właściwości zestawu wierszy za pomocą `CDBPropSet::AddProperty`.

Aby uzyskać informacje na temat atrybutów omówione w tym temacie, zobacz [OLE DB atrybuty konsumentów](../../windows/ole-db-consumer-attributes.md).

> [!NOTE]
> Następujące `include` instrukcje są wymagane do kompilowania w poniższych przykładach:
> ```cpp
> #include <atlbase.h>
> #include <atlplus.h>
> #include <atldbcli.h>
> ```

## <a name="table-and-accessor-declaration-using-attributes"></a>Tabela i deklaracja dostępu przy użyciu atrybutów

Poniższy kod wywoła `db_source` i `db_table` klasy tabeli. `db_source` Określa źródło danych i połączenia ma być używany. `db_table` wprowadza kod odpowiedni szablon, aby zadeklarować klasy tabeli. `db_column` Określ mapę kolumny i wstrzyknąć deklaracji metody dostępu. Atrybuty konsumentów OLE DB można użyć w każdym projekcie, który obsługuje ATL.

Poniżej przedstawiono deklaracji metody dostępu i tabeli przy użyciu atrybutów:

```cpp
//////////////////////////////////////////////////////////////////////
// Table and accessor declaration using attributes
// authors.h
//////////////////////////////////////////////////////////////////////

// Table class declaration
// (Note that you must provide your own connection string for db_source.)
[
   db_source(L"your connection string"),
   db_table("Authors")
]
class CAuthors
{
public:
   DBSTATUS m_dwAuIDStatus;
   DBSTATUS m_dwAuthorStatus;
   DBSTATUS m_dwYearBornStatus;
   DBLENGTH m_dwAuIDLength;
   DBLENGTH m_dwAuthorLength;
   DBLENGTH m_dwYearBornLength;
   [db_column("1", status = "m_dwAuIDStatus", length = "m_dwAuIDLength")] LONG m_AuID;
   [db_column("2", status = "m_dwAuthorStatus", length = "m_dwAuthorLength")] TCHAR m_Author[51];
   [db_column("3", status = "m_dwYearBornStatus", length = "m_dwYearBornLength")] SHORT m_YearBorn;
   void GetRowsetProperties(CDBPropSet* pPropSet)
   {
      pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true);
      pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true);
      pPropSet->AddProperty(DBPROP_IRowsetChange, true);
   }
};
```

## <a name="table-and-accessor-declaration-using-templates"></a>Tabela i deklaracja dostępu za pomocą szablonów

Poniżej przedstawiono deklaracji metody dostępu i tabeli przy użyciu szablonów.

```cpp
//////////////////////////////////////////////////////////////////////
// Table and user record class declaration using templates
// authors.h
//////////////////////////////////////////////////////////////////////

// User record class declaration
class CAuthorsNoAttrAccessor
{
public:
   DWORD m_dwAuIDStatus;
   DWORD m_dwAuthorStatus;
   DWORD m_dwYearBornStatus;
   DWORD m_dwAuIDLength;
   DWORD m_dwAuthorLength;
   DWORD m_dwYearBornLength;
   LONG m_AuID;
   TCHAR m_Author[51];
   SHORT m_YearBorn;
   void GetRowsetProperties(CDBPropSet* pPropSet)
   {
      pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true);
      pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true);
      pPropSet->AddProperty(DBPROP_IRowsetChange, true);
   }
   HRESULT OpenDataSource()
   {
      CDataSource _db;

HRESULT hr;
      hr = _db.OpenFromInitializationString(L"your connection string");
      if (FAILED(hr))
      {
#ifdef _DEBUG
         AtlTraceErrorRecords(hr);
#endif
         return hr;
      }
      return m_session.Open(_db);
   }
   void CloseDataSource()
   {
      m_session.Close();
   }
   operator const CSession&()
   {
      return m_session;
   }
   CSession m_session;
   BEGIN_COLUMN_MAP(CAuthorsNoAttrAccessor)
      COLUMN_ENTRY_LENGTH_STATUS(1, m_AuID, m_dwAuIDLength, m_dwAuIDStatus)
      COLUMN_ENTRY_LENGTH_STATUS(2, m_Author, m_dwAuthorLength, m_dwAuthorStatus)
      COLUMN_ENTRY_LENGTH_STATUS(3, m_YearBorn, m_dwYearBornLength, m_dwYearBornStatus)
   END_COLUMN_MAP()
};
class CAuthorsNoAttr : public CTable<CAccessor<CAuthorsNoAttrAccessor>>
{
public:
   HRESULT OpenAll()
   {
HRESULT hr;
      hr = OpenDataSource();
      if (FAILED(hr))
         return hr;
      __if_exists(GetRowsetProperties)
      {
         CDBPropSet propset(DBPROPSET_ROWSET);
         __if_exists(HasBookmark)
         {
            propset.AddProperty(DBPROP_IRowsetLocate, true);
         }
         GetRowsetProperties(&propset);
         return OpenRowset(&propset);
      }
      __if_not_exists(GetRowsetProperties)
      {
         __if_exists(HasBookmark)
         {
            CDBPropSet propset(DBPROPSET_ROWSET);
            propset.AddProperty(DBPROP_IRowsetLocate, true);
            return OpenRowset(&propset);
         }
      }
      return OpenRowset();
   }
   HRESULT OpenRowset(DBPROPSET *pPropSet = NULL)
   {
HRESULT hr = Open(m_session, "Authors", pPropSet);
#ifdef _DEBUG
      if(FAILED(hr))
         AtlTraceErrorRecords(hr);
#endif
      return hr;
   }
   void CloseAll()
   {
      Close();
      CloseDataSource();
   }
};
```

## <a name="see-also"></a>Zobacz także

[Atrybuty konsumentów OLE DB](../../windows/ole-db-consumer-attributes.md)
