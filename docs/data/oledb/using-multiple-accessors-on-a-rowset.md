---
title: Używanie wielu metod dostępu w zestawie wierszy
ms.date: 10/24/2018
helpviewer_keywords:
- BEGIN_ACCESSOR macro
- BEGIN_ACCESSOR macro, multiple accessors
- rowsets [C++], multiple accessors
- accessors [C++], rowsets
ms.assetid: 80d4dc5d-4940-4a28-a4ee-d8602f71d2a6
ms.openlocfilehash: d1ab314edeebedef4cff14cd5364a7ca16c74769
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033310"
---
# <a name="using-multiple-accessors-on-a-rowset"></a>Używanie wielu metod dostępu w zestawie wierszy

Istnieją trzy podstawowe scenariusze, w których należy użyć wielu metod dostępu:

- **Wiele odczytu/zapisu zestawów wierszy.** W tym scenariuszu masz tabelę z kluczem podstawowym. Chcesz można było odczytać wszystkie kolumny w wierszu, w tym klucza podstawowego. Należy mieć uprawnienia zapisu danych do wszystkich kolumn z wyjątkiem klucza podstawowego (ponieważ nie można zapisać kolumny klucza podstawowego). W takim przypadku można skonfigurować dwie metody dostępu:

  - Akcesor 0 zawiera wszystkie kolumny.

  - Metoda dostępu 1 zawiera wszystkie kolumny z wyjątkiem klucza podstawowego.

- **Wydajność.** W tym scenariuszu co najmniej jedna kolumna ma dużą ilość danych, na przykład grafiki, dźwięku lub wideo pliki. Za każdym razem, gdy przeniesiesz się do wiersza, prawdopodobnie nie chcesz pobrać kolumny z plikiem dużych ilości danych, ponieważ wykonanie tej tak może spowolnić wydajność aplikacji.

  Możesz skonfigurować oddzielne metod dostępu, w których pierwszą metodę dostępu zawiera wszystkie kolumny z wyjątkiem tego, z dużej ilości danych i pobiera dane z tych kolumn automatycznie; pierwszy metody dostępu jest akcesor automatycznie. Druga metoda dostępu pobiera tylko wartości w kolumnie przechowywania dużych ilości danych, ale go nie pobierać dane z tej kolumny automatycznie. Może mieć inne metody aktualizacji lub pobierania dużych ilości danych na żądanie.

  - Akcesor 0 jest automatyczne akcesora; pobiera wszystkie kolumny z wyjątkiem tego, z dużej ilości danych.

  - Metody dostępu 1 nie jest automatyczna akcesora; pobiera kolumnę z dużych ilości danych.

  Argument automatycznego umożliwia określenie, czy akcesor jest akcesora automatycznie.

- **Wiele kolumn ISequentialStream.** W tym scenariuszu masz więcej niż jedną kolumnę gospodarstwa `ISequentialStream` danych. Jednak każdej metody dostępu jest ograniczona do jednego `ISequentialStream` strumienia danych. Aby rozwiązać ten problem, należy skonfigurować kilka metod dostępu, każdego mających jeden `ISequentialStream` wskaźnika.

Zwykle tworzy się przy użyciu metod dostępu [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) i [END_ACCESSOR](../../data/oledb/end-accessor.md) makra. Można również użyć [db_accessor —](../../windows/db-accessor.md) atrybutu. (Metody dostępu są dokładniejszym opisem zawartym w [rekordów użytkowników](../../data/oledb/user-records.md).) Makra lub atrybutu należy określić, czy metoda dostępu jest automatyczne czy akcesor nie automatyczne:

- Automatyczne akcesor przesunięcie w metody takie jak `MoveFirst`, `MoveLast`, `MoveNext`, i `MovePrev` pobierania danych dla wszystkich określonych kolumn automatycznie. Akcesor 0 powinny być automatyczne metody dostępu.

- W metodę dostępu nie automatyczne pobieranie nie występuje, dopóki nie zostanie jawnie wywołać metody takie jak `Update`, `Insert`, `Fetch`, lub `Delete`. W scenariuszach opisanych powyżej nie można pobrać wszystkich kolumn na każdy ruch. Można umieścić co najmniej jedną kolumnę w oddzielnych metody dostępu i upewnij, że akcesor nie automatyczne, jak pokazano poniżej.

W poniższym przykładzie użyto wielu metod dostępu do odczytu i zapisu do tabeli zadań bazy danych programu SQL Server pubs używanie wielu metod dostępu. W tym przykładzie jest najbardziej popularnym zastosowaniem wielu metod dostępu; Zobacz powyższy scenariusz "wiele zestawów wierszy odczytu/zapisu".

Klasa rekord użytkownika jest w następujący sposób. Obejmuje to skonfigurowanie dwóch metod dostępu: akcesor 0 zawiera tylko kolumny klucza podstawowego (identyfikator), a metoda dostępu 1 innych kolumn.

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

Głównego kodu wyglądają następująco. Wywoływanie `MoveNext` automatycznie pobiera dane z Identyfikatora kolumny klucza podstawowego, przy użyciu metody dostępu 0. Uwaga jak `Insert` metoda niemal akcesor używa zakończenia 1 w celu uniknięcia zapisywania kolumna klucza podstawowego.

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

## <a name="see-also"></a>Zobacz także

[Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)<br/>
[Rekordy użytkowników](../../data/oledb/user-records.md)
