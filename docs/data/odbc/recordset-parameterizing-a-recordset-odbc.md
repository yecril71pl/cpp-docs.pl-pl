---
title: 'Zestaw rekordów: parametryzacja zestawu rekordów (ODBC)'
ms.date: 05/09/2019
helpviewer_keywords:
- parameterizing recordsets
- ODBC recordsets, parameterizing
- recordsets, parameterizing
- passing parameters, to queries at runtime
ms.assetid: 7d1dfeb6-5ee0-45e2-aacc-63bc52a465cd
ms.openlocfilehash: 6d28471bdc44d5d75a9eeac2327f92a8e2e265c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360660"
---
# <a name="recordset-parameterizing-a-recordset-odbc"></a>Zestaw rekordów: parametryzacja zestawu rekordów (ODBC)

Ten temat dotyczy klas MFC ODBC.

Czasami możesz chcieć wybrać rekordy w czasie wykonywania, korzystając z informacji obliczonych lub uzyskanych od użytkownika końcowego. Parametry zestawu rekordów umożliwiają osiągnięcie tego celu.

W tym temacie wyjaśniono:

- [Celem sparametryzowanego pliku recordset](#_core_parameterized_recordsets).

- [Kiedy i dlaczego warto sparametryzować plan rekordów](#_core_when_to_use_parameters).

- [Jak zadeklarować elementy członkowskie danych parametrów w klasie zestaw rekordów](#_core_parameterizing_your_recordset_class).

- [Jak przekazać informacje o parametrach do obiektu tablicy rekordów w czasie wykonywania](#_core_passing_parameter_values_at_run_time).

## <a name="parameterized-recordsets"></a><a name="_core_parameterized_recordsets"></a>Rekordy sparametryzowane

Sparametryzowany plik recordset umożliwia przekazywanie informacji o parametrach w czasie wykonywania. Ma to dwa cenne efekty:

- Może to spowodować lepszą szybkość wykonywania.

- Umożliwia tworzenie kwerendy w czasie wykonywania, na podstawie informacji niedostępnych w czasie projektowania, takich jak informacje uzyskane od użytkownika lub obliczone w czasie wykonywania.

Podczas wywoływania `Open` uruchomienia kwerendy, plik recordset używa informacji o parametrach, aby zakończyć jego **SQL SELECT** instrukcji. Można sparametryzować dowolny rekord.

## <a name="when-to-use-parameters"></a><a name="_core_when_to_use_parameters"></a>Kiedy używać parametrów

Typowe zastosowania parametrów obejmują:

- Przekazywanie argumentów w czasie wykonywania do wstępnie zdefiniowanej kwerendy.

   Aby przekazać parametry do procedury składowanej, należy określić pełną niestandardową instrukcję `Open` **ODBC CALL** — z symbolami zastępczymi parametrów — podczas wywoływania, zastępując domyślną instrukcję SQL zestawu rekordów. Aby uzyskać więcej informacji, zobacz [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) in the *Class Library Reference* and [SQL: Customizing Your Recordset's SQL Statement (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md) and [Recordset: Declaring a Class for a Predefined Query (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md).

- Wydajne wykonywanie wielu przekwalić z różnymi informacjami o parametrach.

   Na przykład za każdym razem, gdy użytkownik końcowy wyszukuje informacje dla określonego ucznia w bazie danych rejestracji ucznia, można określić nazwę lub identyfikator ucznia jako parametr uzyskany od użytkownika. Następnie po wywołaniu funkcji członkowskiej elementu rekordu kwerendy `Requery` wybiera tylko rekord tego ucznia.

   Ciąg filtra modułu recordset, przechowywany w `m_strFilter`, może wyglądać następująco:

    ```cpp
    "StudentID = ?"
    ```

   Załóżmy, że w zmiennej `strInputID`uzyskasz identyfikator studenta . Po ustawieniu parametru `strInputID` (na przykład identyfikatora studenta 100) wartość zmiennej jest powiązana z symbolem zastępczym parametru reprezentowanym przez "?" w ciągu filtru.

   Przypisać wartość parametru w następujący sposób:

    ```cpp
    strInputID = "100";
    ...
    m_strParam = strInputID;
    ```

   Nie chcesz skonfigurować ciągu filtru w ten sposób:

    ```cpp
    m_strFilter = "StudentID = 100";   // 100 is incorrectly quoted
                                       // for some drivers
    ```

   Aby zapoznać się z omówieniem prawidłowego używania cudzysłowów dla ciągów filtrów, zobacz [Recordset: Filtering Records (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).

   Wartość parametru jest inna za każdym razem, gdy ponownie podszesisz rekord dla nowego identyfikatora studenta.

   > [!TIP]
   > Korzystanie z parametru jest bardziej wydajne niż tylko filtr. W przypadku sparametryzowanego zestawie rekordów baza danych musi przetworzyć instrukcję SQL **SELECT** tylko raz. W przypadku filtrowanego zestawu rekordów bez parametrów instrukcja `Requery` **SELECT** musi być przetwarzana za każdym razem, gdy zostanie ściągnięta z nową wartością filtru.

Aby uzyskać więcej informacji o filtrach, zobacz [Recordset: Filtering Records (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).

## <a name="parameterizing-your-recordset-class"></a><a name="_core_parameterizing_your_recordset_class"></a>Parametryzacja klasy recordset

> [!NOTE]
> Ta sekcja dotyczy obiektów pochodzących z `CRecordset` których pobieranie wiersza zbiorczego nie zostało zaimplementowane. Jeśli używasz pobierania wiersza zbiorczego, implementowanie parametrów jest podobny proces. Aby uzyskać więcej informacji, zobacz [Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Przed utworzeniem klasy zestawu rekordów należy określić, jakie parametry są potrzebne, jakie są ich typy danych i sposób, w jaki zestaw rekordów ich używa.

#### <a name="to-parameterize-a-recordset-class"></a>Aby sparametryzować klasę tablicy rekordów

> [!NOTE]
> Kreator konsumenta odbc MFC nie jest dostępny w programie Visual Studio 2019 i nowszych. Tę funkcję można utworzyć ręcznie.

1. Uruchom [Kreatora konsumenta MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) z **dodaj klasę,** aby utworzyć klasę.

1. Określ elementy członkowskie danych pól dla kolumn zbioru rekordów.

1. Po kreatora zapisuje klasy do pliku w projekcie, przejdź do pliku .h i ręcznie dodać jeden lub więcej elementów członkowskich danych parametru do deklaracji klasy. Dodatek może wyglądać mniej więcej jak w poniższym przykładzie, część klasy migawki przeznaczonej do odpowiedzi na zapytanie "Którzy uczniowie są w klasie wyższej?"

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

   Dodaj elementy członkowskie danych parametrów po elementach członkowskich danych pola generowanych przez kreatora. Konwencja polega na dokłowie słowa "Param" do każdej nazwy parametru zdefiniowanej przez użytkownika.

1. Zmodyfikuj definicję funkcji elementu członkowskiego [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) w pliku cpp. Dodaj wywołanie funkcji RFX dla każdego elementu członkowskiego danych parametru dodanego do klasy. Aby uzyskać informacje na temat zapisywania funkcji RFX, zobacz [Wymiana pól rekordu: Jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Poprzedzić wywołania RFX dla parametrów za pomocą jednego wywołania:

    ```cpp
    pFX->SetFieldType( CFieldExchange::param );
    // RFX calls for parameter data members
    ```

1. W konstruktorze klasy zestawu rekordów zwiększaj liczbę `m_nParams`parametrów, .

   Aby uzyskać więcej informacji, zobacz [Wymiana pól rekordu: Praca z kodem kreatora](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md).

1. Podczas pisania kodu, który tworzy obiekt recordset tej klasy, miejsce "?" (znak zapytania) symbol w każdym miejscu w ciągu instrukcji SQL, gdzie parametr ma zostać zastąpiony.

   W czasie wykonywania symbole zastępcze "?" są wypełniane w kolejności przez wartości parametrów, które przekazujesz. Pierwszy zestaw elementów członkowskich danych parametru po wywołaniu [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) zastępuje pierwsze "?" w ciągu SQL, drugi element członkowski danych parametru zastępuje drugie "?", i tak dalej.

> [!NOTE]
> Kolejność parametrów jest ważne: kolejność wywołań RFX dla parametrów w `DoFieldExchange` funkcji musi odpowiadać kolejności symboli zastępczych parametrów w ciągu SQL.

> [!TIP]
> Najbardziej prawdopodobnym ciągiem do pracy jest ciąg, który określisz (jeśli istnieje) dla [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) elementu członkowskiego danych klasy, ale niektóre sterowniki ODBC mogą zezwalać na parametry w innych klauzulach SQL.

## <a name="passing-parameter-values-at-run-time"></a><a name="_core_passing_parameter_values_at_run_time"></a>Przekazywanie wartości parametrów w czasie wykonywania

Przed wywołaniem `Open` (dla nowego obiektu pliku recordset) `Requery` lub (dla istniejącego) należy określić wartości parametrów.

#### <a name="to-pass-parameter-values-to-a-recordset-object-at-run-time"></a>Aby przekazać wartości parametrów do obiektu tablicy rekordów w czasie wykonywania

1. Konstruuj obiekt pliku recordset.

1. Przygotuj ciąg lub ciągi, `m_strFilter` takie jak ciąg zawierający instrukcję SQL lub jego części. Umieść symbole zastępcze "?", w których mają być wprowadzane informacje o parametrach.

1. Przypisz wartość parametru czasu wykonywania do każdego elementu członkowskiego danych parametru obiektu.

1. Wywołanie `Open` funkcji elementu `Requery`członkowskiego (lub , dla istniejącego pliku rekordów).

Załóżmy na przykład, że chcesz określić ciąg filtru dla pliku rekordów przy użyciu informacji uzyskanych w czasie wykonywania. Załóżmy, że skonstruowałeś `CStudentSet` recordset `rsStudents` klasy wcześniej — o nazwie — a teraz chcesz go ponownie podzeslić dla określonego rodzaju informacji o uczniu.

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

Zestawu rekordów zawiera rekordy dla tych uczniów, których rekordy spełniają warunki określone przez filtr, który został skonstruowany z parametrów czasu wykonywania. W takim przypadku rekord zawiera rekordy dla wszystkich starszych studentów.

> [!NOTE]
> W razie potrzeby można ustawić wartość elementu członkowskiego danych parametru na Null, używając [SetParamNull](../../mfc/reference/crecordset-class.md#setparamnull). Można również sprawdzić, czy element członkowski danych parametru jest null, przy użyciu [IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull).

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: dodawanie, aktualizowanie i usuwanie rekordów (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)<br/>
[Zestaw rekordów: jak zestawy rekordów pobierają rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)
