---
title: 'Zestaw rekordów: Jak zestawy rekordów pobierają rekordy (ODBC) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- recordsets, selecting records
- record selection, ODBC recordsets
- SQL statements, recordset
- records, selecting
- recordsets, constructing SQL statements
- ODBC recordsets, selecting records
ms.assetid: 343a6a91-aa4c-4ef7-b21f-2f2bfd0d3787
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a9ff2f1e9946eb32356eb09fa2ee216aa636a351
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33093233"
---
# <a name="recordset-how-recordsets-select-records-odbc"></a>Zestaw rekordów: jak zestawy rekordów pobierają rekordy (ODBC)
Ten temat dotyczy klasach MFC ODBC.  
  
 W tym temacie opisano:  
  
-   [Roli i opcje w wybierania rekordów](#_core_your_options_in_selecting_records).  
  
-   [Jak konstruuje jej instrukcji SQL zestawu rekordów i wybiera rekordy](#_core_how_a_recordset_constructs_its_sql_statement).  
  
-   [Co można zrobić, aby dostosować wybór](#_core_customizing_the_selection).  
  
 Zestawy rekordów wybierz rekordy ze źródła danych za pośrednictwem sterownika ODBC przez wysłanie do sterownika instrukcji SQL. SQL wysyłane zależy od tego, jak projektować i otwórz klasy zestawu rekordów.  
  
##  <a name="_core_your_options_in_selecting_records"></a> Opcje w Wybieranie rekordów  
 W poniższej tabeli przedstawiono opcje w wybierania rekordów.  
  
### <a name="how-and-when-you-can-affect-a-recordset"></a>Jak i kiedy może mieć wpływ na zestaw rekordów  
  
|Gdy użytkownik|Można|  
|--------------|-------------|  
|Deklarowanie klasy rekordów z **Dodaj klasę** Kreatora|Określ tabeli, które można wybierać.<br /><br /> Określ kolumn.<br /><br /> Zobacz [Dodawanie klienta MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).|  
|Zakończenie implementacji klasy zestawu rekordów|Zastąpienie takich jak funkcje Członkowskie `OnSetOptions` (zaawansowane), aby ustawić opcje specyficzne dla aplikacji lub zmienić ustawienia domyślne. Określ elementy członkowskie danych parametru, jeśli chcesz sparametryzowane zestaw rekordów.|  
|Konstruowania obiektu zestawu rekordów (przed wywołaniem **Otwórz**)|Określ warunek wyszukiwania (prawdopodobnie złożony) do użycia w **gdzie** klauzuli filtrujące rekordy. Zobacz [zestaw rekordów: filtrowanie rekordów (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).<br /><br /> Określanie kolejności sortowania do użycia w **ORDER BY** klauzuli sortowania rekordów. Zobacz [zestaw rekordów: sortowanie rekordów (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md).<br /><br /> Określ wartości parametrów dla wszystkich parametrów, które dodawana do klasy. Zobacz [zestaw rekordów: parametryzacja zestawu rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).|  

| Uruchom zapytanie w zestawie rekordów przez wywołanie metody **Otwórz**| Określ niestandardowy ciąg SQL, aby zastąpić domyślny ciąg SQL przez kreatora. Zobacz [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) w *klasy odwołanie do biblioteki* i [SQL: dostosowywanie instrukcji SQL zestawu rekordów (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md). |  

| Wywołanie **Requery** do requery rekordów przy użyciu najnowszych wartości w źródle danych | Określ nowe parametry, filtrowania lub sortowania. Zobacz [zestaw rekordów: ponowne wysyłanie zapytania do zestawu rekordów (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md). |  
  
##  <a name="_core_how_a_recordset_constructs_its_sql_statement"></a> Jak zestaw rekordów konstruuje jej instrukcji SQL  
 Podczas wywoływania obiektu zestawu rekordów [Otwórz](../../mfc/reference/crecordset-class.md#open) funkcji członkowskiej **Otwórz** tworzy instrukcję SQL przy użyciu niektóre lub wszystkie następujące składniki:  
  
-   **LpszSQL** parametr przekazany do **Otwórz**. Jeśli nie **NULL**, ten parametr określa niestandardowy ciąg SQL lub jedną część. Platformę analizuje ciąg. Jeśli ciąg jest SQL **wybierz** instrukcji lub ODBC **WYWOŁAĆ** instrukcji, w ramach używa ciągu jako instrukcji SQL zestawu rekordów. Jeśli ciąg rozpoczyna się od "SELECT" lub "{CALL", framework używa co to jest dostarczany do skonstruowania SQL **FROM** klauzuli.  
  
-   Długość ciągu zwróconego przez [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql). Domyślnie jest to nazwa określona dla zestawu rekordów w Kreatorze tabeli, ale można zmienić, funkcja zwraca. Wywołania framework `GetDefaultSQL` — Jeśli ciąg rozpoczyna się od "SELECT" lub "{CALL", jest przyjmowana Nazwa tabeli, który jest używany do tworzenia ciągu SQL.  
  

-   Elementy członkowskie danych pola zestawu rekordów, które mają być powiązane z określonych kolumn tabeli. Platformę wiąże kolumn rekordów adresów tych elementów przy użyciu ich jako buforów. Określa platformę korelację elementy członkowskie danych pola kolumny tabeli z [RFX](../../data/odbc/record-field-exchange-using-rfx.md) lub wywołania funkcji RFX zbiorczego w zestawie rekordów [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) lub [DoBulkFieldExchange ](../../mfc/reference/crecordset-class.md#dofieldexchange) funkcję elementu członkowskiego.  
  
-   [Filtru](../../data/odbc/recordset-filtering-records-odbc.md) dla zestawu rekordów, jeśli taki występuje, zawartych w [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) element członkowski danych. Platformę używa tego ciągu do utworzenia SQL **gdzie** klauzuli.  
  
-   [Sortowania](../../data/odbc/recordset-sorting-records-odbc.md) order dla zestawu rekordów, jeśli istnieje, zawarte w [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) element członkowski danych. Platformę używa tego ciągu do utworzenia SQL **ORDER BY** klauzuli.  

  
    > [!TIP]
    >  Aby użyć SQL **GROUP BY** klauzuli (i prawdopodobnie **HAVING** klauzuli), Dołącz klauzule na końcu ciągu filtru.  
  
-   Wartości dowolnego [elementy członkowskie danych parametru](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) określ dla tej klasy. Ustawianie wartości parametrów tuż przed wywołaniem **Otwórz** lub **Requery**. Platformę wiąże wartości parametru "?" symbole zastępcze w ciągu SQL. W czasie kompilacji można określić ciąg z symbole zastępcze. W czasie wykonywania platformę kopiuje dane na podstawie wartości parametru, który zostanie przekazany.  
  
 **Otwórz** tworzy SQL **wybierz** instrukcji z tych składników. Zobacz [Dostosowywanie zaznaczenie](#_core_customizing_the_selection) szczegółowe informacje o używaniu składników w ramach.  
  
 Po konstruowanie instrukcji, **Otwórz** wysyła SQL do Menedżera sterowników ODBC (i Biblioteka kursorów ODBC, jeśli znajduje się w pamięci), który wysyła się do sterownika ODBC dla określonego systemu DBMS. Sterownik komunikuje się z systemu DBMS przeprowadzenie zaznaczenia w źródle danych i pobiera pierwszy rekord. Platformę ładuje rekordu do elementy członkowskie danych pola zestawu rekordów.  
  
 Można otworzyć kombinacji tych metod [tabel](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md) i utworzyć kwerendy na podstawie [sprzężenia](../../data/odbc/recordset-performing-a-join-odbc.md) z wielu tabel. Z dodatkowe dostosowanie, można wywołać [wstępnie zdefiniowane zapytania](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md) (procedury składowane), wybierz tabeli kolumn nie jest znany w czasie projektowania i [powiązać](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) je do pól rekordów albo można wykonać większość innych dostęp do danych zadania. Nadal można wykonać zadania nie może wykonać dostosowując zestawów rekordów za [wywoływanie funkcji ODBC API](../../data/odbc/odbc-calling-odbc-api-functions-directly.md) lub bezpośrednio wykonywania instrukcji SQL z [CDatabase::ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql).  
  
##  <a name="_core_customizing_the_selection"></a> Dostosowywanie zaznaczenia  
 Oprócz dostarczanie filtru, kolejności sortowania lub parametry, można wykonać następujące czynności, aby dostosować wybór w zestawie rekordów:  
  
-   Przekaż niestandardowy ciąg SQL w **lpszSQL** podczas wywoływania [Otwórz](../../mfc/reference/crecordset-class.md#open) zestawu rekordów. Cokolwiek przekazywane w **lpsqSQL** ma pierwszeństwo przed co [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) zwraca funkcję elementu członkowskiego.  
  
     Aby uzyskać więcej informacji, zobacz [SQL: instrukcji SQL Dostosowywanie Your w zestawie rekordów (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md), który opisano typy instrukcji SQL (lub częściowe instrukcje) można przekazać do **Otwórz** i wykonuje platformę z nimi.  
  
    > [!NOTE]
    >  Niestandardowy ciąg, który zostanie przekazany zaczyna się od "SELECT" lub "{CALL", MFC przyjęto założenie, że zawiera on nazwę tabeli. Dotyczy to również następnego elementu listy punktowane.  
  
-   Instrukcja ALTER ciąg, który kreator zapisuje w twoim zestawie rekordów `GetDefaultSQL` funkcję elementu członkowskiego. Edytuj kod funkcji, aby zmienić go zwraca. Domyślnie kreator zapisuje `GetDefaultSQL` funkcja, która zwraca nazwę jednej tabeli.  
  
     Może mieć `GetDefaultSQL` zwracać elementy, które można przekazać **lpszSQL** parametr **Otwórz**. Jeśli nie przekazuj niestandardowy ciąg SQL w **lpszSQL**, platformę używa ciągu który `GetDefaultSQL` zwraca. Co najmniej `GetDefaultSQL` musi zwracać nazwę jednej tabeli. Ale może być zwracany wiele nazw tabel, pełne **wybierz** instrukcji, ODBC **WYWOŁAĆ** instrukcji i tak dalej. Lista co można przekazać do **lpszSQL** — lub ma `GetDefaultSQL` zwracać — zobacz [SQL: instrukcja SQL Dostosowywanie Your w zestawie rekordów (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).  
  
     Jeśli przeprowadzasz sprzężenia dwóch lub więcej tabel przepisywania `GetDefaultSQL` dostosować listę tabel w SQL używać **FROM** klauzuli. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: wykonywanie Join (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).  
  

-   Ręcznie powiązać pola dodatkowe elementy członkowskie danych, być może na podstawie informacji uzyskać dotyczące schematu źródła danych w czasie wykonywania. Dodaj elementy członkowskie danych pola do klasy rekordów [RFX](../../data/odbc/record-field-exchange-using-rfx.md) lub funkcji RFX zbiorczego wywołuje ich [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) lub [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) funkcji członkowskiej i Inicjowanie danych elementów członkowskich w konstruktorze klasy. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: dynamiczne wiązanie danych kolumn (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
-   Zastąpienie funkcji elementów członkowskich zestawu rekordów, takich jak `OnSetOptions`, aby ustawić opcje specyficzne dla aplikacji, lub aby zastąpić wartości domyślne.  
  
 Jeśli chcesz utworzyć zestaw rekordów na złożonych instrukcji SQL, należy użyć kombinacji tych metod dostosowywania. Na przykład może chcesz używać klauzuli SQL i słowa kluczowe nieobsługiwana bezpośrednio przez zestawy rekordów lub być może musisz się wiele tabel.  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Zestaw rekordów: Jak zestawy rekordów aktualizują rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)   
 [Podstawy ODBC](../../data/odbc/odbc-basics.md)   
 [SQL](../../data/odbc/sql.md)   
 [Zestaw rekordów: blokowanie rekordów (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)