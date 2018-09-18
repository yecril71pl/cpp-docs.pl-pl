---
title: 'Zestaw rekordów: Parametryzacja zestawu rekordów (ODBC) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parameterizing recordsets
- ODBC recordsets, parameterizing
- recordsets, parameterizing
- passing parameters, to queries at runtime
ms.assetid: 7d1dfeb6-5ee0-45e2-aacc-63bc52a465cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4689207264fb4c07158fa9c97df0e9b431fba6d3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077226"
---
# <a name="recordset-parameterizing-a-recordset-odbc"></a>Zestaw rekordów: parametryzacja zestawu rekordów (ODBC)

Ten temat dotyczy klas MFC ODBC.  
  
Czasami możesz chcieć mieć możliwość wyboru rekordów w czasie wykonywania, korzystając z informacji, które mają być obliczane lub uzyskany ze użytkownikowi końcowemu. Parametry zestawu rekordów pozwalają osiągnąć ten cel.  
  
W tym temacie opisano:  
  
- [Celem sparametryzowane rekordów](#_core_parameterized_recordsets).  
  
- [Kiedy i dlaczego warto parametryzacja zestawu rekordów](#_core_when_to_use_parameters).  
  
- [Jak zadeklarować parametr elementów członkowskich danych w swojej klasie rekordów](#_core_parameterizing_your_recordset_class).  
  
- [Jak przekazać informacje o parametrach na obiekt zestawu rekordów w czasie wykonywania](#_core_passing_parameter_values_at_run_time).  
  
##  <a name="_core_parameterized_recordsets"></a> Sparametryzowany zestawów rekordów  

Zestaw rekordów sparametryzowanych pozwala przekazać informacje o parametrach w czasie wykonywania. To ma dwa skutki przydatne:  
  
- Może to spowodować zwiększenia szybkości wykonywania.  
  
- Dzięki temu można utworzyć zapytanie w czasie wykonywania, w oparciu o informacje, które nie są dostępne dla użytkownika w czasie projektowania, takich jak informacje uzyskane za pomocą użytkownika lub obliczane w czasie wykonywania.  
  
Gdy wywołujesz `Open` Aby uruchomić zapytanie, zestaw rekordów używa informacji parametru do ukończenia jej **SQL ZAZNACZYĆ** instrukcji. Możecie żadnych rekordów.  
  
##  <a name="_core_when_to_use_parameters"></a> Kiedy należy używać parametrów  

Typowe zastosowania dla parametrów obejmują:  
  
- Przekazywanie argumentów czasu wykonywania dla wstępnie zdefiniowanego zapytania.  
  
     Do przekazania parametrów do procedury składowanej, należy określić pełną ODBC niestandardowe **WYWOŁANIA** instrukcji — z symbolami zastępczymi parametru — gdy wywołujesz `Open`, Zastępowanie domyślnego instrukcji SQL zestawu rekordów. Aby uzyskać więcej informacji, zobacz [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) w *odwołanie do biblioteki klas* i [SQL: dostosowywanie Your zestawu rekordów instrukcji SQL (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md) i [ Zestaw rekordów: Deklarowanie klasy dla wstępnie zdefiniowanego zapytania (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md).  

  
- Wydajne wykonywanie wielu requeries z informacjami o różnych parametrów.  
  
     Na przykład każdym razem, gdy użytkownikowi końcowemu wyszukuje informacje dotyczące określonego dla uczniów w bazie danych rejestracji dla uczniów, użytkownika studenta nazwa lub identyfikator jako parametr uzyskanych od użytkownika. Następnie, gdy zostanie wywołana w zestawie rekordów `Requery` funkcji członkowskiej, zapytanie wybiera tylko Studenta dla tego rekordu.  
  
     Ciąg filtru zestawu rekordów, przechowywane w `m_strFilter`, może wyglądać następująco:  
  
    ```  
    "StudentID = ?"  
    ```  
  
     Załóżmy, że można uzyskać Identyfikatora dla uczniów w zmiennej `strInputID`. Po ustawieniu wartości parametru na `strInputID` (na przykład dla uczniów w identyfikatorze 100) wartość zmiennej jest powiązany z reprezentowany przez symbol zastępczy parametrów "?" w ciągu filtru.  
  
     Przypisz wartość parametru w następujący sposób:  
  
    ```  
    strInputID = "100";  
    ...  
    m_strParam = strInputID;  
    ```  
  
     Czy chcesz skonfigurować ciągu filtru w ten sposób:  
  
    ```  
    m_strFilter = "StudentID = 100";   // 100 is incorrectly quoted  
                                       // for some drivers  
    ```  
  
     Omówienie sposobu użycia oferty poprawnie dla filtru ciągów, zobacz [zestaw rekordów: filtrowanie rekordów (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).  
  
     Wartość parametru różni się każdorazowo Requery — zestaw rekordów dla nowego identyfikatora dla uczniów.  
  
    > [!TIP]
    >  Za pomocą parametru jest bardziej wydajne niż po prostu filtru. Dla sparametryzowane zestawu rekordów bazy danych musi przetworzyć SQL **wybierz** instrukcji tylko raz. Dla filtrowanego zestawu rekordów bez parametrów **wybierz** instrukcja musi zostać przetworzona, każdym razem `Requery` z nową wartością filtru.  
  
Aby uzyskać więcej informacji na temat filtrów, zobacz [zestaw rekordów: filtrowanie rekordów (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).  
  
##  <a name="_core_parameterizing_your_recordset_class"></a> Parametryzacja zestawu rekordów klasy  
  
> [!NOTE]
>  Ta sekcja jest stosowana do obiektów pochodzących od `CRecordset` w wierszu zbiorczego, które podczas pobierania nie została zaimplementowana. Jeśli używasz wiersz zbiorcze pobieranie, implementowanie parametrów jest podobny proces. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
Przed przystąpieniem do tworzenia klasy zestawu rekordów, należy określić parametry potrzebne, jakie są typy danych i jak zestaw rekordów są one używane.  
  
#### <a name="to-parameterize-a-recordset-class"></a>Definiowanie parametrów klasy zestawu rekordów  
  
1. Uruchom [Kreator użytkownika interfejsu ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) z **Dodaj klasę** Aby utworzyć klasę.  
  
1. Określ elementy członkowskie danych pola dla kolumn w zestawie rekordów.  
  
1. Po kreator zapisuje klasy w pliku w projekcie, przejdź do pliku .h, a następnie ręcznie dodać elementy członkowskie danych parametru co najmniej jeden z deklaracją klasy. Dodanie może wyglądać jak w poniższym przykładzie, część klasy migawki mają odpowiedzieć na kwerendę "oznaczają uczniów w klasie starszy?"  
  
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
  
     Dodaj swoje elementy członkowskie danych parametru po elementy członkowskie danych pola generowane przez kreatora. Konwencji jest Dołącz słowo "Param" do nazwy parametrów zdefiniowanych przez użytkownika.  
  
1. Modyfikowanie [dofieldexchange —](../../mfc/reference/crecordset-class.md#dofieldexchange) definicji funkcji składowej w pliku .cpp. Dodaj wywołanie funkcji RFX dla każdego parametru element członkowski danych dodane do klasy. Informacje na temat pisania funkcji RFX, zobacz [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Należy poprzedzić wywołania RFX parametrów za pomocą pojedynczego wywołania do:  
  
    ```  
    pFX->SetFieldType( CFieldExchange::param );  
    // RFX calls for parameter data members  
    ```  
  
1. W konstruktorze klasy zestawu rekordów, zwiększ liczbę parametrów, `m_nParams`.  
  
     Aby uzyskać informacje, zobacz [wymiana pól rekordów: Praca z kodem kreatora](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md).  
  
1. Kiedy piszesz kod, który tworzy zestaw rekordów obiekt tej klasy, umieść "?" symbol (znak zapytania) w obu miejscach Twoimi ciągami instrukcji SQL, w którym ma zostać zastąpiony parametrem.  
  
     W czasie wykonywania "?" symbole zastępcze są wypełniane, kolejność, według wartości parametrów możesz przekazać. Pierwszy element członkowski danych parametru ustawić po [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) wywołanie zamienia pierwszy "?"w parametrach SQL drugi element członkowski danych parametru zastępuje drugi"?", i tak dalej.  
  
> [!NOTE]
>  Ważna jest kolejność parametrów: kolejność RFX wywołuje parametrów w swojej `DoFieldExchange` funkcja musi być zgodna z kolejnością parametr symbole zastępcze w ciągu SQL.  
  
> [!TIP]

>  Najbardziej prawdopodobną ciąg do pracy z jest ciągiem, o których należy określić (jeśli istnieje) dla tej klasy [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) element członkowski danych, ale niektóre sterowniki ODBC mogą zezwalać na parametry w innych klauzul SQL.  
  
##  <a name="_core_passing_parameter_values_at_run_time"></a> Przekazywanie wartości parametrów w czasie wykonywania  

Należy określić wartości parametrów, zanim wywołasz `Open` (dla nowego obiektu zestawu rekordów) lub `Requery` (na jeden z istniejących).  
  
#### <a name="to-pass-parameter-values-to-a-recordset-object-at-run-time"></a>Aby przekazać wartości parametru na obiekt zestawu rekordów w czasie wykonywania  
  
1. Skonstruuj obiekt zestawu rekordów.  
  
1. Przygotowanie ciągu lub ciągów, takich jak `m_strFilter` ciąg zawierający instrukcję SQL lub jej części. Umieść "?" informacje o parametrach w przypadku przejść symbole zastępcze.  
  
1. Przypisać wartość parametru uruchomieniowego każdy element członkowski danych parametr obiektu.  
  
1. Wywołaj `Open` funkcji składowej (lub `Requery`, dla istniejącego zestawu rekordów).  
  
Załóżmy na przykład, aby określić ciąg filtru dla rekordów przy użyciu informacji uzyskanych w czasie wykonywania. Przyjęto założenie, zostały zbudowane zestaw rekordów klasy `CStudentSet` wcześniej — nazywane `rsStudents` — a teraz chcą ją dla określonego rodzaju informacjami o uczniach requery.  
  
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
  
Zestaw rekordów zawiera rekordy dla tych studentów, w której rekordy spełniają warunków określonych przez jeden filtr, który został zbudowany z parametrów czasu wykonywania. W tym przypadku zestaw rekordów zawiera rekordy dla wszystkich studentów starszy.  
  
> [!NOTE]
>  Jeśli to konieczne, można ustawić wartości element członkowski danych parametru na wartość Null, za pomocą [SetParamNull](../../mfc/reference/crecordset-class.md#setparamnull). Możesz również sprawdzić, czy element członkowski danych parametr ma wartość Null, za pomocą [IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull).  
  
## <a name="see-also"></a>Zobacz też  

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: dodawanie, aktualizowanie i usuwanie rekordów (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)<br/>
[Zestaw rekordów: jak zestawy rekordów pobierają rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)