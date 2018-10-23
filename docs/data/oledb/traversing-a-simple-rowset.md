---
title: Przechodzenie przez prosty zestaw wierszy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/19/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- data access [C++], rowsets
- rowsets [C++], accessing
- simple rowsets
- OLE DB consumers [C++], database attributes
- accessors [C++], rowsets
ms.assetid: b45acf16-4029-429d-ab8d-b7fba98b9740
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 62a1b6c0aa164e6b564c505873fbc85f38b9febf
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808319"
---
# <a name="traversing-a-simple-rowset"></a>Przechodzenie przez prosty zestaw wierszy

Poniższy przykład pokazuje dostęp szybkie i łatwe bazy danych, która nie zawiera polecenia. Poniższy kod konsumenta w projekcie ATL, pobiera rekordy z tabeli o nazwie *artystów* w programie Microsoft Access bazy danych przy użyciu dostawcy Microsoft OLE DB dla ODBC. Ten kod tworzy [CTable](../../data/oledb/ctable-class.md) obiektu tabeli za pomocą metody dostępu na podstawie użytkownika rekordu klasy `CArtists`. Otwiera połączenie, otwiera sesji na połączenie i otwiera tabelę w sesji.  
  
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
  
Rekord użytkownika `CArtists`, wygląda następująco:  
  
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