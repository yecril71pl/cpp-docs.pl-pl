---
title: "Używanie wielu metod dostępu w zestawie wierszy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- BEGIN_ACCESSOR macro
- BEGIN_ACCESSOR macro, multiple accessors
- rowsets [C++], multiple accessors
- accessors [C++], rowsets
ms.assetid: 80d4dc5d-4940-4a28-a4ee-d8602f71d2a6
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b50604feb05609e15fbc0f241d297c8661efa00b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="using-multiple-accessors-on-a-rowset"></a>Używanie wielu metod dostępu w zestawie wierszy
Istnieją trzy podstawowe scenariusze, w których należy użyć wielu metod dostępu:  
  
-   **Wiele odczytu/zapisu zestawów wierszy.** W tym scenariuszu istnieje tabela o kluczu podstawowym. Chcesz mieć możliwość odczytu wszystkich kolumn w wierszu, włączając klucz podstawowy. Należy mieć możliwość zapisywania danych do wszystkich kolumn z wyjątkiem klucza podstawowego (ponieważ nie można zapisać kolumna klucza podstawowego). W takim przypadku można skonfigurować dwie metody dostępu:  
  
    -   Metoda dostępu 0 zawiera wszystkie kolumny.  
  
    -   Metoda dostępu 1 zawiera wszystkie kolumny z wyjątkiem klucza podstawowego.  
  
-   **Wydajność.** W tym scenariuszu jeden lub więcej kolumn zawierają dużą ilość danych, na przykład grafiki, plików audio i wideo. Za każdym razem, gdy zostanie przeniesiony do wiersza, prawdopodobnie nie chcesz pobrać kolumny z plikiem dużej ilości danych, ponieważ spowoduje to może spowolnić wydajności aplikacji.  
  
     Możesz skonfigurować oddzielne metod dostępu, w których pierwszego dostępu zawiera wszystkich kolumn, oprócz jednego z dużej ilości danych, a jego pobiera dane z tych kolumn automatycznie; jest to akcesor automatycznie. Druga metoda dostępu pobiera tylko kolumnę zawierającą dużej ilości danych, ale go nie pobiera dane z tej kolumny automatycznie. Może mieć inne metody aktualizacji lub pobrać dużej ilości danych na żądanie.  
  
    -   Metoda dostępu 0 jest automatyczne akcesora; pobiera on wszystkich kolumn, oprócz jednego z dużej ilości danych.  
  
    -   Metoda dostępu 1 nie jest automatyczne akcesora; pobiera on kolumna o dużej ilości danych.  
  
     Aby określić, czy akcesor jest to metoda dostępu automatycznie, użyj argumentu automatycznie.  
  
-   **Wiele kolumn ISequentialStream.** W tym scenariuszu użytkownik ma więcej niż jednej kolumny zawierające `ISequentialStream` danych. Jednak każdy akcesor jest tylko jeden `ISequentialStream` strumienia danych. Aby rozwiązać ten problem, skonfiguruj kilka metod dostępu, każdy zawiera jedną `ISequentialStream` wskaźnika.  
  
 Zwykle tworzy się przy użyciu metody dostępu [begin_accessor —](../../data/oledb/begin-accessor.md) i [END_ACCESSOR](../../data/oledb/end-accessor.md) makra. Można również użyć [db_accessor —](../../windows/db-accessor.md) atrybutu. (Metody dostępu są opisane dalej w [rekordów użytkowników](../../data/oledb/user-records.md).) Makra lub atrybut Określ, czy metoda dostępu jest automatyczne czy akcesor nie automatyczne:  
  
-   W metodzie dostępu automatyczne, Przenieś metody takie jak **MoveFirst**, `MoveLast`, `MoveNext`, i `MovePrev` pobieranie danych dla wszystkich określonych kolumn automatycznie. Akcesor 0 powinny być automatyczne metody dostępu.  
  
-   W metodę dostępu-automatyczne pobieranie przeprowadzona dopiero po jawnie wywołania metody takie jak **aktualizacji**, **Wstaw**, **pobrać**, lub **usunąć**. W opisanych powyżej scenariuszy nie można pobrać wszystkich kolumn w każdym ruchu. Można umieścić co najmniej jedną kolumnę w oddzielnych metody dostępu i upewnij, że akcesor nie automatyczne, jak pokazano poniżej.  
  
 W poniższym przykładzie użyto wielu metod dostępu do odczytu i zapisu do tabeli zadań bazy danych programu SQL Server pubs używanie wielu metod dostępu. Jest to najbardziej typowe użycie wielu metod dostępu; zobacz scenariusz "wiele zestawów wierszy odczytu/zapisu" powyżej.  
  
 Klasy rekordów użytkowników ma następującą składnię. Konfiguruje dwie metody dostępu: akcesor 0 zawiera tylko kolumna klucza podstawowego (ID), a akcesor 1 innych kolumn.  
  
```  
class CJobs  
{  
public:  
    enum {  
        sizeOfDescription = 51  
    };  
  
    short nID;  
    char szDescription[ sizeOfDescription ];  
    short nMinLvl;  
    short nMaxLvl;  
  
    DWORD dwID;  
    DWORD dwDescription;  
    DWORD dwMinLvl;  
    DWORD dwMaxLvl;  
  
BEGIN_ACCESSOR_MAP(CJobs, 2)  
    // Accessor 0 is the automatic accessor  
    BEGIN_ACCESSOR(0, true)  
        COLUMN_ENTRY_STATUS(1, nID, dwID)  
    END_ACCESSOR()  
    // Accessor 1 is the non-automatic accessor  
    BEGIN_ACCESSOR(1, true)  
        COLUMN_ENTRY_STATUS(2, szDescription, dwDescription)  
        COLUMN_ENTRY_STATUS(3, nMinLvl, dwMinLvl)  
        COLUMN_ENTRY_STATUS(4, nMaxLvl, dwMaxLvl)  
    END_ACCESSOR()  
END_ACCESSOR_MAP()  
};  
```  
  
 Główne kod ma następującą składnię. Wywoływanie `MoveNext` automatycznie pobiera dane z Identyfikatora kolumny klucza podstawowego, przy użyciu metody dostępu 0. Uwaga jak **Wstaw** metody niemal dostępu końcowe zastosowania 1, aby uniknąć zastępowania do kolumny klucza podstawowego.  
  
```  
int main(int argc, char* argv[])  
{  
    // Initalize COM  
    ::CoInitialize(NULL);  
  
    // Create instances of the data source and session  
    CDataSource source;  
    CSession session;  
    HRESULT hr = S_OK;  
  
    // Set initialization properties  
    CDBPropSet dbinit(DBPROPSET_DBINIT);  
    dbinit.AddProperty(DBPROP_AUTH_USERID, OLESTR("my_user_id"));  
    dbinit.AddProperty(DBPROP_INIT_CATALOG, OLESTR("pubs"));  
    dbinit.AddProperty(DBPROP_INIT_DATASOURCE, OLESTR("(local)"));  
  
    hr = source.Open("SQLOLEDB.1", &dbinit);  
    if (hr == S_OK)  
    {  
        hr = session.Open(source);  
        if (hr == S_OK)  
        {  
            // Ready to fetch/access data  
            CTable<CAccessor<CJobs> > jobs;  
  
            // Set properties for making the rowset a read/write cursor  
            CDBPropSet dbRowset(DBPROPSET_ROWSET);  
            dbRowset.AddProperty(DBPROP_CANFETCHBACKWARDS, true);  
            dbRowset.AddProperty(DBPROP_CANSCROLLBACKWARDS, true);  
            dbRowset.AddProperty(DBPROP_IRowsetChange, true);  
            dbRowset.AddProperty(DBPROP_UPDATABILITY,  
                DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE |  
                DBPROPVAL_UP_DELETE);  
  
            hr = jobs.Open(session, "jobs", &dbRowset);  
            if (hr == S_OK)  
            {  
                // Calling MoveNext automatically retrieves ID  
                // (using accessor 0)  
                while(jobs.MoveNext() == S_OK)  
                   printf_s("Description = %s\n", jobs.szDescription);  
  
                hr = jobs.MoveFirst();  
                if (hr == S_OK)  
                {  
                    jobs.nID = 25;  
                    strcpy_s(&jobs.szDescription[0],  
                             jobs.sizeOfDescription,  
                             "Developer");  
                    jobs.nMinLvl = 10;  
                    jobs.nMaxLvl = 20;  
  
                    jobs.dwDescription = DBSTATUS_S_OK;  
                    jobs.dwID = DBSTATUS_S_OK;  
                    jobs.dwMaxLvl = DBSTATUS_S_OK;  
                    jobs.dwMinLvl = DBSTATUS_S_OK;  
  
                    // Insert method uses accessor 1  
                    // (to avoid writing to the primary key column)  
                    hr = jobs.Insert(1);     
                }  
                jobs.Close();  
            }  
            session.Close();  
        }  
        source.Close();  
    }  
  
    // Uninitialize COM  
    ::CoUninitialize();  
    return 0;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)   
 [Rekordy użytkowników](../../data/oledb/user-records.md)