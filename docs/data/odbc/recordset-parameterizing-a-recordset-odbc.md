---
title: "Zestaw rekordów: Parametryzacja zestawu rekordów (ODBC) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- parameterizing recordsets
- ODBC recordsets, parameterizing
- recordsets, parameterizing
- passing parameters, to queries at runtime
ms.assetid: 7d1dfeb6-5ee0-45e2-aacc-63bc52a465cd
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 38b17950a7aaf89cc041c4933768bf6b2da0c9b0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-parameterizing-a-recordset-odbc"></a>Zestaw rekordów: parametryzacja zestawu rekordów (ODBC)
Ten temat dotyczy klasach MFC ODBC.  
  
 Czasami może chcesz mieć możliwość wyboru rekordów w czasie wykonywania, przy użyciu informacji ma obliczonych lub otrzymanych od użytkownika końcowego. Zestaw rekordów parametry umożliwiają realizację tego celu.  
  
 W tym temacie opisano:  
  
-   [Celem sparametryzowane rekordów](#_core_parameterized_recordsets).  
  
-   [Kiedy i dlaczego warto parametryzacja zestawu rekordów](#_core_when_to_use_parameters).  
  
-   [Jak zadeklarować parametru elementy członkowskie danych w klasie rekordów](#_core_parameterizing_your_recordset_class).  
  
-   [Sposób przekazywania informacji o parametrach na obiekt zestawu rekordów w czasie wykonywania](#_core_passing_parameter_values_at_run_time).  
  
##  <a name="_core_parameterized_recordsets"></a>Sparametryzowane zestawy rekordów  
 Sparametryzowane rekordów umożliwia przekazywanie informacji o parametrach w czasie wykonywania. Ma to dwa cenne skutki:  
  
-   Może to spowodować zwiększenia szybkości wykonywania.  
  
-   Dzięki temu można tworzyć zapytania w czasie wykonywania na podstawie informacji nie jest dostępny dla użytkownika w czasie projektowania, takie jak informacje uzyskane z użytkownikiem lub obliczane w czasie wykonywania.  
  
 Podczas wywoływania **Otwórz** Aby uruchomić zapytanie, zestawu rekordów używa informacji parametru do ukończenia jej **SQL SELECT** instrukcji. Można parametryzacja żadnych rekordów.  
  
##  <a name="_core_when_to_use_parameters"></a>Kiedy należy używać parametrów  
 Typowym zastosowaniem parametrów obejmują:  
  
-   Przekazywanie argumentów czasu wykonywania dla wstępnie zdefiniowanego zapytania.  
  
     Do przekazania parametrów do procedury składowanej, należy określić pełną ODBC niestandardowych **WYWOŁAĆ** instrukcji — z parametru symbole zastępcze — podczas wywoływania **Otwórz**, zastępowanie domyślną instrukcję SQL w zestawie rekordów. Aby uzyskać więcej informacji, zobacz [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) w *informacje dotyczące biblioteki klas* i [SQL: instrukcja SQL Dostosowywanie Your w zestawie rekordów (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md) i [ Zestaw rekordów: Deklarowanie klasy dla wstępnie zdefiniowanego zapytania (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md).  

  
-   Wydajne wykonywanie wielu requeries z innym parametrem informacji.  
  
     Na przykład zawsze, gdy użytkownikowi końcowemu wyszukuje informacje dotyczące konkretnego uczniów w bazie danych rejestracji dla użytkowników domowych, można określić nazwę lub identyfikator Studenta jako parametr uzyskane od użytkownika. Następnie, gdy jest wywoływana w zestawie rekordów **Requery** funkcji członkowskiej, zapytanie wybiera tylko Studenta dla tego rekordu.  
  
     Ciąg filtru zestawu rekordów, przechowywane w **m_strFilter**, może wyglądać następująco:  
  
    ```  
    "StudentID = ?"  
    ```  
  
     Załóżmy, że można uzyskać Identyfikatora uczniów w zmiennej `strInputID`. Jeśli parametr jest ustawiony na `strInputID` powiązany (np. studentów identyfikator 100) symbol zastępczy parametru reprezentowanego przez wartość zmiennej "?" w ciągu filtru.  
  
     Przypisz wartości parametru w następujący sposób:  
  
    ```  
    strInputID = "100";  
    ...  
    m_strParam = strInputID;  
    ```  
  
     Czy chcesz skonfigurować ciąg filtru w ten sposób:  
  
    ```  
    m_strFilter = "StudentID = 100";   // 100 is incorrectly quoted  
                                       // for some drivers  
    ```  
  
     Omówienie sposobu użycia cudzysłowy poprawnie filtru ciągów, zobacz [zestaw rekordów: filtrowanie rekordów (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).  
  
     Wartość parametru jest inny za każdym razem requery zestaw rekordów dla nowego identyfikatora studenta.  
  
    > [!TIP]
    >  Za pomocą parametru jest bardziej efektywne niż po prostu filtru. Dla sparametryzowane zestawu rekordów, bazy danych musi przetworzyć SQL **wybierz** instrukcji tylko raz. Dla filtrowanego zestawu rekordów bez parametrów **wybierz** musi zostać przetworzona instrukcja każdej aktualizacji **Requery** z nową wartością filtru.  
  
 Aby uzyskać więcej informacji na temat filtrów, zobacz [zestaw rekordów: filtrowanie rekordów (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).  
  
##  <a name="_core_parameterizing_your_recordset_class"></a>Ustawianie klasy zestawu rekordów  
  
> [!NOTE]
>  Ta sekcja dotyczy obiektów pochodzących od `CRecordset` w wiersz, który zbiorczego pobierania nie została zaimplementowana. Jeśli używasz wiersza zbiorcze pobieranie, wdrażanie parametrów jest podobnej procedury. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Przed utworzeniem klasy zestawu rekordów, określić parametrów, jakie należy, co to są typy danych i jak zestaw rekordów używa ich.  
  
#### <a name="to-parameterize-a-recordset-class"></a>Definiowanie parametrów klasy zestawu rekordów  
  
1.  Uruchom [Kreator konsumenta MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) z **Dodaj klasę** Aby utworzyć klasę.  
  
2.  Określ elementy członkowskie danych pola dla kolumn w zestawie rekordów.  
  
3.  Po kreator zapisuje klasy w pliku w projekcie, przejdź do pliku .h i ręcznie dodać co najmniej jednego członka danych parametru do deklaracji klasy. Dodanie może wyglądać jak w następującym przykładzie, część klasy migawki przeznaczone do odpowiedzi na zapytanie "będące studentów w klasie wyższych?"  
  
    ```  
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
  
     Dodaj użytkownika elementy członkowskie danych parametru po elementy członkowskie danych pola generowane przez kreatora. Konwencji jest Dołącz słowo "Param" do nazwy parametrów zdefiniowanych przez użytkownika.  
  
4.  Modyfikowanie [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) definicji funkcji członkowskiej w pliku .cpp. Dodaj wywołanie funkcji RFX dla każdego elementu członkowskiego danych parametru, który dodawana do klasy. Informacje na temat pisania funkcji RFX, zobacz [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Należy poprzedzić wywołania RFX parametrów przy użyciu jednego wywołania do:  
  
    ```  
    pFX->SetFieldType( CFieldExchange::param );  
    // RFX calls for parameter data members  
    ```  
  
5.  W konstruktorze klasy zestawu rekordów, należy zwiększyć liczbę parametrów, `m_nParams`.  
  
     Aby uzyskać informacje, zobacz [wymiana pól rekordów: Praca z kodem kreatora](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md).  
  
6.  Podczas pisania kodu, który tworzy obiekt zestawu rekordów tej klasy, umieść "?" symbol (znak zapytania) w obu miejscach z ciągów instrukcji SQL, w którym ma zostać zastąpiony parametrem.  
  
     W czasie wykonywania "?" symbole zastępcze są wypełniane, kolejność, według wartości parametru przekazać. Wartość pierwszego elementu członkowskiego danych parametru po [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) wywołania zamienia pierwszy "?"w ciągu SQL, drugi element członkowski danych parametru zastępuje drugi"?" i tak dalej.  
  
> [!NOTE]
>  Ważna jest kolejność parametrów: kolejność RFX wymaga parametrów w Twojej `DoFieldExchange` funkcji muszą być zgodne kolejność parametrów symbole zastępcze w ciągu SQL.  
  
> [!TIP]

>  Najprawdopodobniej ciąg do pracy z jest ciągiem, możesz określić (jeśli istnieją) dla tej klasy [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) element członkowski danych, ale niektóre sterowniki ODBC może umożliwić parametrów w klauzulach innych SQL.  
  
##  <a name="_core_passing_parameter_values_at_run_time"></a>Przekazywanie wartości parametrów w czasie wykonywania  
 Należy określić wartości parametrów przed wywołaniem **Otwórz** (dla nowego obiektu zestawu rekordów) lub **Requery** (dla istniejącego).  
  
#### <a name="to-pass-parameter-values-to-a-recordset-object-at-run-time"></a>Aby podać wartości parametrów na obiekt zestawu rekordów w czasie wykonywania  
  
1.  Konstruowania obiektu zestawu rekordów.  
  
2.  Przygotowanie ciąg lub ciągów, takich jak **m_strFilter** ciąg zawierający instrukcję SQL lub jej części. Umieść "?" symbole zastępcze informacje o parametrach w przypadku przejść.  
  
3.  Do każdego elementu członkowskiego danych parametru obiektu, należy przypisać wartość parametru czasu wykonywania.  
  
4.  Wywołanie **Otwórz** funkcji członkowskiej (lub **Requery**, dla istniejącego zestawu rekordów).  
  
 Załóżmy na przykład, aby określić ciąg filtru dla zestawu rekordów przy użyciu informacji uzyskanych w czasie wykonywania. Założono zbudowania rekordów klasy `CStudentSet` wcześniej — nazywany `rsStudents` — a teraz chcesz requery dla określonego rodzaju informacje dla użytkowników domowych.  
  
```  
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
  
 Zestaw rekordów zawiera rekordy te studentów rekordów spełnia warunki określone przez filtr, który został skonstruowany na podstawie parametrów czasu wykonywania. W takim przypadku zestaw rekordów zawiera rekordy, dla wszystkich studentów wyższych szczebli.  
  
> [!NOTE]
>  W razie potrzeby można ustawić wartości elementu członkowskiego danych parametru na wartość Null, za pomocą [SetParamNull](../../mfc/reference/crecordset-class.md#setparamnull). Można również sprawdzić, czy element członkowski danych parametr ma wartość Null, za pomocą [IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull).  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Zestaw rekordów: Dodawanie, aktualizowanie i usuwanie rekordów (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)   
 [Zestaw rekordów: jak zestawy rekordów pobierają rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)