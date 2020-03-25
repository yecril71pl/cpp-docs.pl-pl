---
title: 'Zestaw rekordów: jak zestawy rekordów pobierają rekordy (ODBC)'
ms.date: 05/09/2019
helpviewer_keywords:
- recordsets, selecting records
- record selection, ODBC recordsets
- SQL statements, recordset
- records, selecting
- recordsets, constructing SQL statements
- ODBC recordsets, selecting records
ms.assetid: 343a6a91-aa4c-4ef7-b21f-2f2bfd0d3787
ms.openlocfilehash: 252d17fc56c13415f1068d6b16ed8b1ee663b5f1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212891"
---
# <a name="recordset-how-recordsets-select-records-odbc"></a>Zestaw rekordów: jak zestawy rekordów pobierają rekordy (ODBC)

> [!NOTE]
> Kreator użytkownika ODBC MFC nie jest dostępny w programie Visual Studio 2019 i nowszych. Nadal można utworzyć konsumenta ręcznie.

Ten temat dotyczy klas MFC ODBC.

W tym temacie objaśniono:

- [Twoja rola i opcje w obszarze Wybieranie rekordów](#_core_your_options_in_selecting_records).

- [Jak zestaw rekordów tworzy instrukcję SQL i wybiera rekordy](#_core_how_a_recordset_constructs_its_sql_statement).

- [Co można zrobić, aby dostosować wybór](#_core_customizing_the_selection).

Zestawy rekordów wybierają rekordy ze źródła danych za pośrednictwem sterownika ODBC, wysyłając instrukcje SQL do sterownika. Wysłany kod SQL zależy od sposobu projektowania i otwierania klasy zestawu rekordów.

##  <a name="your-options-in-selecting-records"></a><a name="_core_your_options_in_selecting_records"></a>Opcje wybierania rekordów

W poniższej tabeli przedstawiono opcje wyboru rekordów.

### <a name="how-and-when-you-can-affect-a-recordset"></a>Jak i kiedy można mieć wpływ na zestaw rekordów

|Jeśli|Można|
|--------------|-------------|
|Deklarowanie klasy zestawu rekordów przy użyciu kreatora **dodawania klasy**|Określ, z której tabeli chcesz wybrać.<br /><br /> Określ kolumny, które mają zostać uwzględnione.<br /><br /> Zobacz [Dodawanie użytkownika MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).|
|Ukończ implementację klasy zestawu rekordów|Przesłoń funkcje członkowskie, takie jak `OnSetOptions` (Zaawansowane), aby ustawić opcje specyficzne dla aplikacji lub zmienić ustawienia domyślne. Określ elementy członkowskie danych parametru, jeśli chcesz użyć sparametryzowanego zestawu rekordów.|
|Konstruowanie obiektu zestawu rekordów (przed wywołaniem `Open`)|Określ warunek wyszukiwania (prawdopodobnie złożony) do użycia w klauzuli **WHERE** , która filtruje rekordy. Zobacz [zestaw rekordów: filtrowanie rekordów (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).<br /><br /> Określ kolejność sortowania, która ma być używana w klauzuli **order by** , która sortuje rekordy. Zobacz [zestaw rekordów: sortowanie rekordów (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md).<br /><br /> Określ wartości parametrów dla dowolnych parametrów dodanych do klasy. Zobacz [zestaw rekordów: parametryzacja a zestaw rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).|

| Uruchom kwerendę zestawu rekordów, wywołując `Open`| Określ niestandardowy ciąg SQL, aby zastąpić domyślny ciąg SQL skonfigurowany przez kreatora. Zobacz [CRecordset:: Open](../../mfc/reference/crecordset-class.md#open) w *bibliotece klas dokumentacja* i [SQL: dostosowywanie instrukcji SQL zestawu rekordów (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md). |

| Wywołaj `Requery`, aby ponownie wykonać kwerendę zestawu rekordów przy użyciu najnowszych wartości ze źródła danych | Określ nowe parametry, filtr lub Sortuj. Zobacz [zestaw rekordów: badanie zestawu rekordów (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md). |

##  <a name="how-a-recordset-constructs-its-sql-statement"></a><a name="_core_how_a_recordset_constructs_its_sql_statement"></a>Jak zestaw rekordów tworzy instrukcję SQL

Gdy wywołujesz funkcję [Open](../../mfc/reference/crecordset-class.md#open) member obiektu zestawu rekordów, `Open` konstruuje instrukcję SQL przy użyciu niektórych lub wszystkich następujących składników:

- Parametr *lpszSQL* przeszedł do `Open`. Jeśli wartość nie jest równa NULL, ten parametr określa niestandardowy ciąg SQL lub część jednego. Struktura analizuje ciąg. Jeśli ciąg jest instrukcją SQL **SELECT** lub instrukcją ODBC **call** , struktura używa ciągu jako instrukcji SQL zestawu rekordów. Jeśli ciąg nie zaczyna się od "SELECT" lub "{CALL", struktura używa tego, co podano, aby utworzyć klauzulę SQL **from** .

- Ciąg zwracany przez [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql). Domyślnie jest to nazwa tabeli, która została określona dla zestawu rekordów w kreatorze, ale można zmienić wartość zwracaną przez funkcję. Struktura wywołuje `GetDefaultSQL` — Jeśli ciąg nie zaczyna się od "SELECT" lub "{CALL", zakłada się, że jest nazwą tabeli, która jest używana do konstruowania ciągu SQL.

- Elementy członkowskie danych pola zestawu rekordów, które mają być powiązane z określonymi kolumnami tabeli. Platforma tworzy powiązanie kolumn rekordów z adresami tych elementów członkowskich przy użyciu ich jako buforów. Struktura określa korelację elementów członkowskich danych pól z kolumnami tabeli z wywołań funkcji [RFX](../../data/odbc/record-field-exchange-using-rfx.md) lub bulk RFX w funkcji składowej [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) lub [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) zestawu rekordów.

- [Filtr](../../data/odbc/recordset-filtering-records-odbc.md) zestawu rekordów (jeśli istnieje) zawarty w elemencie członkowskim danych [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) . Struktura używa tego ciągu, aby utworzyć klauzulę **WHERE** języka SQL.

- Porządek [sortowania](../../data/odbc/recordset-sorting-records-odbc.md) zestawu rekordów (jeśli istnieje) zawarty w elemencie członkowskim danych [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) . Struktura używa tego ciągu do konstruowania klauzuli **order by** języka SQL.

   > [!TIP]
   > Aby użyć klauzuli **Group by** SQL (i prawdopodobnie klauzuli **HAVING** ), Dołącz klauzule do końca ciągu filtru.

- Wartości wszystkich [elementów członkowskich danych parametrów](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) określonych dla klasy. Wartości parametrów są ustawiane tuż przed wywołaniem `Open` lub `Requery`. Struktura wiąże wartości parametrów z symbolami zastępczymi "?" w ciągu SQL. W czasie kompilacji należy określić ciąg z symbolami zastępczymi. W czasie wykonywania, struktura wypełnia szczegóły na podstawie wartości parametrów, które są przekazywane.

`Open` konstruuje instrukcję **SELECT** języka SQL z tych składników. Zobacz [Dostosowywanie zaznaczenia,](#_core_customizing_the_selection) Aby uzyskać szczegółowe informacje o tym, jak struktura używa składników programu.

Po skonstruowaniu instrukcji `Open` wysyła dane SQL do Menedżera sterowników ODBC (i biblioteki kursora ODBC, jeśli znajduje się w pamięci), co powoduje wysłanie go do sterownika ODBC dla danego systemu DBMS. Sterownik komunikuje się z systemem DBMS w celu przeprowadzenia wyboru w źródle danych i pobrania pierwszego rekordu. Struktura ładuje rekord do elementów członkowskich danych pola zestawu rekordów.

Można użyć kombinacji tych technik do otwierania [tabel](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md) i konstruowania zapytania na podstawie [sprzężenia](../../data/odbc/recordset-performing-a-join-odbc.md) wielu tabel. Za pomocą dodatkowego dostosowania można wywoływać [wstępnie zdefiniowane zapytania](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md) (procedury składowane), wybierać kolumny tabeli nieznane w czasie projektowania i [powiązać](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) je z polami zestawu rekordów lub wykonywać większość innych zadań dostępu do danych. Zadania, których nie można osiągnąć przez dostosowanie zestawów rekordów, można nadal zrealizować przez [wywoływanie funkcji ODBC API](../../data/odbc/odbc-calling-odbc-api-functions-directly.md) lub bezpośrednie wykonywanie instrukcji SQL z [CDatabase:: ExecuteSql by](../../mfc/reference/cdatabase-class.md#executesql).

##  <a name="customizing-the-selection"></a><a name="_core_customizing_the_selection"></a>Dostosowywanie zaznaczenia

Oprócz dostarczania filtru, kolejności sortowania lub parametrów, można wykonać następujące czynności, aby dostosować wybór zestawu rekordów:

- Przekaż niestandardowy ciąg SQL w *lpszSQL* po wywołaniu metody [Open](../../mfc/reference/crecordset-class.md#open) dla zestawu rekordów. Wszystko, co zostało przekazane w *lpsqSQL* , ma pierwszeństwo przed funkcją składową [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) .

   Aby uzyskać więcej informacji, zobacz [SQL: dostosowywanie instrukcji SQL zestawu rekordów (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md), która opisuje typy instrukcji SQL (lub instrukcji częściowych), które można przekazać do `Open` i jakie są z nimi struktury.

    > [!NOTE]
    >  Jeśli przekazany ciąg niestandardowy nie zaczyna się od "SELECT" lub "{CALL", MFC zakłada, że zawiera nazwę tabeli. Dotyczy to również następnego punktowanego elementu.

- Zmień ciąg, który kreator zapisuje w `GetDefaultSQL` funkcji składowej zestawu rekordów. Edytuj kod funkcji, aby zmienić to, co zwraca. Domyślnie kreator zapisuje funkcję `GetDefaultSQL`, która zwraca nazwę pojedynczej tabeli.

   Możesz mieć `GetDefaultSQL` zwracać wszystkie elementy, które można przekazać do parametru *lpszSQL* , aby `Open`. Jeśli nie przekażesz niestandardowego ciągu SQL w *lpszSQL*, struktura używa ciągu, który zwraca `GetDefaultSQL`. Co najmniej `GetDefaultSQL` musi zwracać nazwę pojedynczej tabeli. Można jednak zwrócić wiele nazw tabel, instrukcję Full **SELECT** , instrukcję ODBC **call** i tak dalej. Aby uzyskać listę elementów, które można przekazać do *lpszSQL* — lub uzyskać `GetDefaultSQL` zwrócić — zobacz [SQL: dostosowywanie instrukcji SQL zestawu rekordów (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

   Jeśli wykonujesz sprzężenie co najmniej dwóch tabel, Zapisz `GetDefaultSQL`, aby dostosować listę tabel używaną w klauzuli SQL **from** . Aby uzyskać więcej informacji, zobacz [zestaw rekordów: wykonywanie sprzężenia (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).

- Ręcznie Powiąż dodatkowe składowe danych pól, na przykład na podstawie uzyskanych informacji o schemacie źródła danych w czasie wykonywania. Należy dodać elementy członkowskie danych pola do klasy zestawu rekordów, [RFX](../../data/odbc/record-field-exchange-using-rfx.md) lub bulk RFX wywołań funkcji dla nich do funkcji składowej [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) lub [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) , a także zainicjować składowe danych w konstruktorze klas. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: dynamiczne wiązanie kolumn danych (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

- Przesłoń funkcje składowe zestawu rekordów, takie jak `OnSetOptions`, aby ustawić opcje specyficzne dla aplikacji lub przesłonić ustawienia domyślne.

Jeśli chcesz oprzeć zestaw rekordów na złożonej instrukcji SQL, musisz użyć kilku kombinacji tych technik dostosowywania. Na przykład może być konieczne użycie klauzul SQL i słów kluczowych, które nie są bezpośrednio obsługiwane przez zestawy rekordów, lub prawdopodobnie są przyłączane do wielu tabel.

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: jak zestawy rekordów aktualizują rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[Podstawy ODBC](../../data/odbc/odbc-basics.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[Zestaw rekordów: blokowanie rekordów (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
