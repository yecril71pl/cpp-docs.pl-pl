---
title: Używanie wielu metod dostępu w zestawie wierszy
ms.date: 10/24/2018
helpviewer_keywords:
- BEGIN_ACCESSOR macro
- BEGIN_ACCESSOR macro, multiple accessors
- rowsets [C++], multiple accessors
- accessors [C++], rowsets
ms.assetid: 80d4dc5d-4940-4a28-a4ee-d8602f71d2a6
ms.openlocfilehash: 48772539b4dda9262a244506a36932d1e752949e
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509407"
---
# <a name="using-multiple-accessors-on-a-rowset"></a>Używanie wielu metod dostępu w zestawie wierszy

Istnieją trzy podstawowe scenariusze, w których należy użyć wielu metod dostępu:

- **Wiele zestawów wierszy do odczytu i zapisu.** W tym scenariuszu masz tabelę z kluczem podstawowym. Chcesz mieć możliwość odczytywania wszystkich kolumn w wierszu, w tym klucza podstawowego. Warto również mieć możliwość zapisu danych do wszystkich kolumn z wyjątkiem klucza podstawowego (ponieważ nie można zapisywać w kolumnie klucza podstawowego). W takim przypadku należy skonfigurować dwie metody dostępu:

  - Metoda dostępu 0 zawiera wszystkie kolumny.

  - Metoda dostępu 1 zawiera wszystkie kolumny poza kluczem podstawowym.

- **Skuteczności.** W tym scenariuszu co najmniej jedna kolumna zawiera dużą ilość danych, na przykład pliki grafiki, dźwięku lub wideo. Za każdym razem, gdy przejdziesz do wiersza, prawdopodobnie nie chcesz pobierać kolumny przy użyciu dużego pliku danych, ponieważ spowodowałoby to zmniejszenie wydajności aplikacji.

  Można skonfigurować oddzielne metody dostępu, w których pierwszy akcesor zawiera wszystkie kolumny z wyjątkiem tych, które mają duże dane, i automatycznie pobiera dane z tych kolumn; pierwszym akcesorem jest metoda autouzupełniania. Druga metoda dostępu pobiera tylko kolumnę przechowującą duże ilości danych, ale nie pobiera danych z tej kolumny automatycznie. Dostępne są inne metody aktualizowania lub pobierania dużych ilości danych na żądanie.

  - Metoda dostępu 0 jest automatycznym akcesorem; Pobiera wszystkie kolumny z wyjątkiem tych z dużą ilością danych.

  - Metoda dostępu 1 nie jest automatycznym akcesorem; Pobiera kolumnę z dużymi danymi.

  Użyj argumentu Auto, aby określić, czy metoda dostępu jest metodą autouzupełniania.

- **Wiele kolumn ISequentialStream.** W tym scenariuszu masz więcej niż jedną kolumnę przechowującą `ISequentialStream` dane. Jednak każdy akcesor jest ograniczony do jednego `ISequentialStream` strumienia danych. Aby rozwiązać ten problem, należy skonfigurować kilka metod dostępu, z których każdy ma jeden `ISequentialStream` wskaźnik.

Zwykle tworzysz metody dostępu przy użyciu makr [BEGIN_ACCESSOR](./macros-and-global-functions-for-ole-db-consumer-templates.md#begin_accessor) i [END_ACCESSOR](./macros-and-global-functions-for-ole-db-consumer-templates.md#end_accessor) . Można również użyć atrybutu [db_accessor](../../windows/attributes/db-accessor.md) . (Metody dostępu są szczegółowo opisane w [rekordach użytkowników](../../data/oledb/user-records.md)). Makra lub atrybut określają, czy metoda dostępu jest metodą automatyczną, czy nieautomatyczną:

- W automatycznej metodzie dostępu można przenosić metody, takie jak `MoveFirst` ,, `MoveLast` `MoveNext` i `MovePrev` pobierać dane dla wszystkich określonych kolumn automatycznie. Akcesor 0 powinien być automatycznym akcesorem.

- W nieautomatycznym akcesorze pobieranie nie odbywa się, dopóki nie zostanie jawnie wywołana metoda, taka jak `Update` ,, `Insert` `Fetch` lub `Delete` . W opisanych powyżej scenariuszach może nie być konieczne pobieranie wszystkich kolumn przy każdym przeniesieniu. Można umieścić co najmniej jedną kolumnę w oddzielnym metodzie dostępu i utworzyć niestandardową metodę dostępu, jak pokazano poniżej.

W poniższym przykładzie użyto wielu metod dostępu do odczytu i zapisu w tabeli Jobs bazy danych SQL Server pubs przy użyciu wielu metod dostępu. Ten przykład jest najbardziej typowym zastosowaniem wielu metod dostępu. Zapoznaj się z scenariuszem "wiele zestawów wierszy do odczytu/zapisu" powyżej.

Klasa rekordu użytkownika jest następująca. Ustawia dwie metody dostępu: akcesor 0 zawiera tylko kolumnę klucza podstawowego (ID) i metodę dostępu 1 zawierają inne kolumny.

```cpp
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

Kod główny jest następujący: Wywołanie `MoveNext` automatycznego pobiera dane z identyfikatora kolumny klucza podstawowego przy użyciu metody dostępu 0. Zwróć uwagę, jak `Insert` Metoda blisko końca używa metody dostępu 1, aby uniknąć zapisywania do kolumny klucza podstawowego.

```cpp
int main(int argc, char* argv[])
{
    // Initialize COM
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
            CTable<CAccessor<CJobs>> jobs;

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

[Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)<br/>
[Rekordy użytkowników](../../data/oledb/user-records.md)
