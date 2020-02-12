---
title: Przechodzenie przez prosty zestaw wierszy
ms.date: 10/19/2018
helpviewer_keywords:
- data access [C++], rowsets
- rowsets [C++], accessing
- simple rowsets
- OLE DB consumers [C++], database attributes
- accessors [C++], rowsets
ms.assetid: b45acf16-4029-429d-ab8d-b7fba98b9740
ms.openlocfilehash: 874c8372074838cd614d1fe17727871ca6e5f21a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127645"
---
# <a name="traversing-a-simple-rowset"></a>Przechodzenie przez prosty zestaw wierszy

Poniższy przykład pokazuje szybki i łatwy dostęp do bazy danych, który nie obejmuje poleceń. Poniższy kod klienta w projekcie ATL pobiera rekordy z tabeli o nazwie *artyści* w bazie danych programu Microsoft Access za pomocą dostawcy OLE DB firmy Microsoft dla ODBC. Kod tworzy obiekt tabeli [CTable](../../data/oledb/ctable-class.md) z akcesorem opartym na klasie rekordu użytkownika `CArtists`. Spowoduje to otwarcie połączenia, otwarcie sesji w ramach połączenia i otwarcie tabeli w sesji.

```cpp
#include <atldbcli.h>
#include <iostream>

using namespace std;

int main()
{
    CDataSource connection;
    CSession session;
    CTable<CAccessor<CArtists>> artists;

    LPCSTR clsid; // Initialize CLSID_MSDASQL here
    LPCTSTR pName = L"NWind";

    // Open the connection, session, and table, specifying authentication
    // using Windows NT integrated security. Hard-coding a password is a major
    // security weakness.
    connection.Open(clsid, pName, NULL, NULL, DBPROP_AUTH_INTEGRATED);

    session.Open(connection);

    artists.Open(session, "Artists");

    // Get data from the rowset
    while (artists.MoveNext() == S_OK)
    {
       cout << artists.m_szFirstName;
       cout << artists.m_szLastName;
    }

    return 0;
}
```

Rekord użytkownika, `CArtists`, wygląda podobnie do tego przykładu:

```cpp
class CArtists
{
public:
// Data Elements
   CHAR m_szFirstName[20];
   CHAR m_szLastName[30];
   short m_nAge;

// Column binding map
BEGIN_COLUMN_MAP(CArtists)
   COLUMN_ENTRY(1, m_szFirstName)
   COLUMN_ENTRY(2, m_szLastName)
   COLUMN_ENTRY(3, m_nAge)
END_COLUMN_MAP()
};
```

## <a name="see-also"></a>Zobacz też

[Praca z szablonami konsumentów OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)