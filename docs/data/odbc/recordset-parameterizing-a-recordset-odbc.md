---
title: 'Zestaw rekordów: parametryzacja zestawu rekordów (ODBC)'
ms.date: 05/09/2019
helpviewer_keywords:
- parameterizing recordsets
- ODBC recordsets, parameterizing
- recordsets, parameterizing
- passing parameters, to queries at runtime
ms.assetid: 7d1dfeb6-5ee0-45e2-aacc-63bc52a465cd
ms.openlocfilehash: ec4198c283700daa2e02e2507b9874eaf02858e9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212813"
---
# <a name="recordset-parameterizing-a-recordset-odbc"></a>Zestaw rekordów: parametryzacja zestawu rekordów (ODBC)

Ten temat dotyczy klas MFC ODBC.

Czasami może być konieczne wybranie rekordów w czasie wykonywania przy użyciu informacji obliczonych lub uzyskanych od użytkownika końcowego. Parametry zestawu rekordów pozwalają osiągnąć ten cel.

W tym temacie objaśniono:

- [Przeznaczenie sparametryzowanego zestawu rekordów](#_core_parameterized_recordsets).

- [Kiedy i dlaczego warto Sparametryzuj zestaw rekordów](#_core_when_to_use_parameters).

- [Jak zadeklarować elementy członkowskie danych parametrów w klasie zestawu rekordów](#_core_parameterizing_your_recordset_class).

- [Jak przekazać informacje o parametrach do obiektu zestawu rekordów w czasie wykonywania](#_core_passing_parameter_values_at_run_time).

##  <a name="parameterized-recordsets"></a><a name="_core_parameterized_recordsets"></a>Zestawy rekordów sparametryzowane

Zestaw rekordów sparametryzowane umożliwia przekazywanie informacji o parametrach w czasie wykonywania. Ma to dwa cenne efekty:

- Może to skutkować lepszą szybkością wykonywania.

- Umożliwia utworzenie zapytania w czasie wykonywania na podstawie informacji, które nie są dostępne w czasie projektowania, takich jak informacje uzyskane od użytkownika lub obliczone w czasie wykonywania.

Gdy wywołasz `Open` do uruchomienia zapytania, zestaw rekordów używa informacji o parametrach do wykonania instrukcji **SELECT języka SQL** . Można Sparametryzuj dowolny zestaw rekordów.

##  <a name="when-to-use-parameters"></a><a name="_core_when_to_use_parameters"></a>Kiedy używać parametrów

Typowe zastosowania parametrów obejmują:

- Przekazywanie argumentów czasu wykonywania do wstępnie zdefiniowanego zapytania.

   Aby przekazać parametry do procedury składowanej, należy określić kompletną instrukcję niestandardowego **wywołania** ODBC — z symbolami zastępczymi parametrów — w przypadku wywołania `Open`, zastępując domyślną instrukcję SQL zestawu rekordów. Aby uzyskać więcej informacji, zobacz [CRecordset:: Open](../../mfc/reference/crecordset-class.md#open) w *dokumentacji biblioteki klas* i [SQL: dostosowywanie instrukcji SQL zestawu rekordów (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md) i [zestawu rekordów: deklarowanie klasy dla wstępnie zdefiniowanego zapytania (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md).

- Wydajne wykonywanie wielu rezapytań z innymi informacjami o parametrach.

   Na przykład za każdym razem, gdy użytkownik końcowy wyszukuje informacje dla konkretnego ucznia w bazie danych rejestracji ucznia, można określić nazwę lub identyfikator ucznia jako parametr uzyskany od użytkownika. Następnie, gdy wywołasz funkcję członkowską `Requery` zestawu rekordów, zapytanie wybiera tylko rekord tego ucznia.

   Ciąg filtru zestawu rekordów, przechowywany w `m_strFilter`, może wyglądać następująco:

    ```cpp
    "StudentID = ?"
    ```

   Załóżmy, że otrzymujesz identyfikator ucznia w zmiennej `strInputID`. Po ustawieniu parametru na `strInputID` (na przykład Identyfikator studenta 100) wartość zmiennej jest powiązana z symbolem zastępczym parametru reprezentowanego przez "?" w ciągu filtru.

   Przypisz wartość parametru w następujący sposób:

    ```cpp
    strInputID = "100";
    ...
    m_strParam = strInputID;
    ```

   Nie chcesz konfigurować ciągu filtru w ten sposób:

    ```cpp
    m_strFilter = "StudentID = 100";   // 100 is incorrectly quoted
                                       // for some drivers
    ```

   Aby poznać sposób poprawnego używania cudzysłowów dla ciągów filtru, zobacz [zestaw rekordów: filtrowanie rekordów (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).

   Wartość parametru jest różna za każdym razem, gdy tworzysz ponownie zestaw rekordów dla nowego identyfikatora ucznia.

   > [!TIP]
   > Użycie parametru jest wydajniejsze niż po prostu filtrem. Dla sparametryzowanego zestawu rekordów baza danych musi przetworzyć instrukcję **SELECT** języka SQL tylko raz. Dla filtrowanego zestawu rekordów bez parametrów instrukcja **SELECT** musi być przetwarzana za każdym razem, gdy `Requery` z nową wartością filtru.

Aby uzyskać więcej informacji o filtrach, zobacz [zestaw rekordów: filtrowanie rekordów (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).

##  <a name="parameterizing-your-recordset-class"></a><a name="_core_parameterizing_your_recordset_class"></a>Parametryzacja klasy zestawu rekordów

> [!NOTE]
> Ta sekcja ma zastosowanie do obiektów pochodnych `CRecordset`, w których nie zaimplementowano pobierania wierszy zbiorczych. Jeśli używasz pobierania wierszy zbiorczych, implementacja parametrów jest podobnym procesem. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Przed utworzeniem klasy zestawu rekordów należy określić parametry, które są potrzebne, jakie są typy danych, oraz sposób ich używania przez zestaw rekordów.

#### <a name="to-parameterize-a-recordset-class"></a>Aby Sparametryzuj klasę zestawu rekordów

> [!NOTE]
> Kreator użytkownika ODBC MFC nie jest dostępny w programie Visual Studio 2019 i nowszych. Tę funkcję można nadal utworzyć ręcznie.

1. Uruchom [Kreatora użytkownika ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) z **klasy Dodaj** , aby utworzyć klasę.

1. Określ elementy członkowskie danych pola dla kolumn zestawu rekordów.

1. Po zapisaniu klasy przez kreatora do pliku w projekcie, przejdź do pliku. h i ręcznie Dodaj jeden lub więcej elementów danych parametrów do deklaracji klasy. Dodanie może wyglądać podobnie do poniższego przykładu, części klasy migawek zaprojektowanej do odpowiedzi na zapytanie "które uczniowie znajdują się w starszej klasie"?

    ```cpp
    class CStudentSet : public CRecordset
    {
    // Field/Param Data
        CString m_strFirstName;
        CString m_strLastName;
        CString m_strStudentID;
        CString m_strGradYear;

        CString m_strGradYrParam;
    };
    ```

   Dodaj elementy członkowskie danych parametru po elementach członkowskich danych pól generowanych przez kreatora. Konwencją jest dołączenie słowa "param" do każdej nazwy parametru zdefiniowanego przez użytkownika.

1. Zmodyfikuj definicję funkcji składowej [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) w pliku CPP. Dodaj wywołanie funkcji RFX dla każdego elementu członkowskiego danych parametru, który został dodany do klasy. Aby uzyskać informacje na temat pisania funkcji usługi RFX, zobacz temat [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Przed RFX wywołań parametrów z pojedynczym wywołaniem do:

    ```cpp
    pFX->SetFieldType( CFieldExchange::param );
    // RFX calls for parameter data members
    ```

1. W konstruktorze klasy zestawu rekordów Zwiększ liczbę parametrów, `m_nParams`.

   Aby uzyskać więcej informacji, zobacz temat [wymiana pól rekordów: Praca z kodem kreatora](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md).

1. Podczas pisania kodu, który tworzy obiekt zestawu rekordów tej klasy, umieść "?" symbol (znak zapytania) w każdym miejscu w ciągu instrukcji SQL, w którym ma zostać zastąpiony parametr.

   W czasie wykonywania symbole zastępcze "?" są wypełniane w kolejności według wartości parametrów, które są przekazywane. Pierwszy parametr elementu członkowskiego danych po wywołaniu [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) zastępuje pierwszy "?" w ciągu SQL, drugi element członkowski danych parametrów zastępuje drugi "?" itd.

> [!NOTE]
> Kolejność parametrów jest ważna: kolejność RFX wywołań parametrów w funkcji `DoFieldExchange` musi być zgodna z kolejnością symboli zastępczych parametrów w ciągu SQL.

> [!TIP]
> Najbardziej prawdopodobną przyczyną działania jest ciąg określony (jeśli istnieje) dla elementu członkowskiego danych klasy [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) , ale niektóre sterowniki ODBC mogą zezwalać na parametry w innych klauzulach SQL.

##  <a name="passing-parameter-values-at-run-time"></a><a name="_core_passing_parameter_values_at_run_time"></a>Przekazywanie wartości parametrów w czasie wykonywania

Należy określić wartości parametrów przed wywołaniem `Open` (dla nowego obiektu zestawu rekordów) lub `Requery` (dla istniejącej).

#### <a name="to-pass-parameter-values-to-a-recordset-object-at-run-time"></a>Aby przekazać wartości parametrów do obiektu zestawu rekordów w czasie wykonywania

1. Konstruowanie obiektu zestawu rekordów.

1. Przygotuj ciąg lub ciągi, takie jak ciąg `m_strFilter`, zawierający instrukcję SQL lub jej części. Umieść symbole zastępcze "?", w których mają zostać umieszczone informacje o parametrach.

1. Przypisz wartość parametru Run-Time do każdego elementu członkowskiego danych parametru obiektu.

1. Wywołaj `Open` funkcję członkowską (lub `Requery`, dla istniejącego zestawu rekordów).

Załóżmy na przykład, że chcesz określić ciąg filtru dla zestawu rekordów przy użyciu informacji uzyskanych w czasie wykonywania. Załóżmy, że skonstruowano zestaw rekordów klasy `CStudentSet` wcześniej — nazywane `rsStudents` — i teraz chcesz ponownie utworzyć jego kwerendę dla określonego rodzaju informacji ucznia.

```cpp
// Set up a filter string with
// parameter placeholders
rsStudents.m_strFilter = "GradYear <= ?";

// Obtain or calculate parameter values
// to pass--simply assigned here
CString strGradYear = GetCurrentAcademicYear( );

// Assign the values to parameter data members
rsStudents.m_strGradYrParam = strGradYear;

// Run the query
if( !rsStudents.Requery( ) )
    return FALSE;
```

Zestaw rekordów zawiera rekordy dla studentów, których rekordy spełniają warunki określone przez filtr, który został skonstruowany z parametrów czasu wykonywania. W tym przypadku zestaw rekordów zawiera rekordy dla wszystkich wyższych uczniów.

> [!NOTE]
>  W razie potrzeby można ustawić wartość elementu członkowskiego danych parametru na wartość null przy użyciu [SetParamNull](../../mfc/reference/crecordset-class.md#setparamnull). Możesz również sprawdzić, czy element członkowski danych parametru ma wartość null, przy użyciu [IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull).

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: dodawanie, aktualizowanie i usuwanie rekordów (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)<br/>
[Zestaw rekordów: jak zestawy rekordów pobierają rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)
