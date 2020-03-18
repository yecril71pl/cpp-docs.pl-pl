---
title: Upraszczanie dostępu do danych za pomocą atrybutów bazy danych
ms.date: 10/19/2018
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
ms.openlocfilehash: 5fc30596058271523f64cc9108ee6f39eb5016fa
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444133"
---
# <a name="simplifying-data-access-with-database-attributes"></a>Upraszczanie dostępu do danych za pomocą atrybutów bazy danych

W tym temacie pokazano, jak używać atrybutów bazy danych, aby uprościć operacje bazy danych.

Podstawowym sposobem uzyskiwania dostępu do informacji z bazy danych jest utworzenie klasy polecenia (lub tabeli) i klasy rekordu użytkownika dla określonej tabeli w bazie danych. Atrybuty bazy danych upraszczają niektóre deklaracje szablonu, które wcześniej należały wykonać.

Aby zademonstrować użycie atrybutów bazy danych, w poniższych sekcjach przedstawiono dwie równoważne deklaracje dotyczące klas i rekordów użytkowników: pierwszy używa atrybutów, a drugi używa szablonów OLE DB. Taki kod deklaracji jest zwykle umieszczany w pliku nagłówkowym o nazwie dla obiektu tabeli lub polecenia, na przykład autors. h.

Porównując dwa pliki, można zobaczyć, jak dużo łatwiej jest używać atrybutów. Różnice są następujące:

- Przy użyciu atrybutów należy tylko zadeklarować jedną klasę: `CAuthors`, ale z szablonami należy zadeklarować dwa: `CAuthorsNoAttrAccessor` i `CAuthorsNoAttr`.

- Wywołanie `db_source` w wersji z atrybutami jest równoważne wywołaniu `OpenDataSource()` w deklaracji szablonu.

- Wywołanie `db_table` w wersji z atrybutami jest równoważne następującej deklaracji szablonu:

    ```cpp
    class CAuthorsNoAttr : public CTable<CAccessor<CAuthorsNoAttrAccessor>>
    ```

- Wywołania `db_column` w wersji z atrybutami są równoważne z mapą kolumn (zobacz `BEGIN_COLUMN_MAP ... END_COLUMN_MAP`) w deklaracji szablonu.

Atrybuty wstrzyknąć deklarację klasy rekordu użytkownika. Klasa rekordu użytkownika jest równa `CAuthorsNoAttrAccessor` w deklaracji szablonu. Jeśli Klasa tabeli jest `CAuthors`, wprowadzona Klasa rekordu użytkownika ma nazwę `CAuthorsAccessor`i można ją wyświetlić tylko w wstrzykiwanym kodzie. Aby uzyskać więcej informacji, zobacz "klasy rekordów użytkowników z Wstrzykiwanymi atrybutami" w [rekordach użytkowników](../../data/oledb/user-records.md).

W obu atrybutach i kodzie z szablonem, należy ustawić właściwości zestawu wierszy przy użyciu `CDBPropSet::AddProperty`.

Aby uzyskać informacje o atrybutach omawianych w tym temacie, zobacz [OLE DB atrybuty konsumentów](../../windows/ole-db-consumer-attributes.md).

> [!NOTE]
> Następujące instrukcje `include` są wymagane do skompilowania przykładów poniżej:

> ```cpp
> #include <atlbase.h>
> #include <atlplus.h>
> #include <atldbcli.h>
> ```

## <a name="table-and-accessor-declaration-using-attributes"></a>Deklaracja tabeli i metody dostępu przy użyciu atrybutów

Poniższy kod wywołuje `db_source` i `db_table` klasy Table. `db_source` określa źródło danych i połączenie, które ma być używane. `db_table` wstrzyknąć odpowiedni kod szablonu, aby zadeklarować klasę tabeli. `db_column` określić mapę kolumn i wstrzyknąć deklarację metody dostępu. W każdym projekcie, który obsługuje ATL, można użyć atrybutów klienta OLE DB.

Oto deklaracja tabeli i metody dostępu przy użyciu atrybutów:

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

## <a name="table-and-accessor-declaration-using-templates"></a>Deklaracja tabeli i metody dostępu przy użyciu szablonów

Oto deklaracja tabeli i metody dostępu przy użyciu szablonów.

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

## <a name="see-also"></a>Zobacz też

[Atrybuty konsumentów OLE DB](../../windows/ole-db-consumer-attributes.md)
