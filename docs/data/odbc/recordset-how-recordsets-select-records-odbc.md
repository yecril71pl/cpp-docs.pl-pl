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
ms.openlocfilehash: 0aa9c082d2d04416358d948476f2ae0f9e2a35af
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366986"
---
# <a name="recordset-how-recordsets-select-records-odbc"></a>Zestaw rekordów: jak zestawy rekordów pobierają rekordy (ODBC)

> [!NOTE]
> Kreator konsumenta odbc MFC nie jest dostępny w programie Visual Studio 2019 i nowszych. Nadal można utworzyć konsumenta ręcznie.

Ten temat dotyczy klas MFC ODBC.

W tym temacie wyjaśniono:

- [Twoja rola i opcje w wybieraniu rekordów](#_core_your_options_in_selecting_records).

- [Jak zestawie rekordów konstruuje swoją instrukcję SQL i wybiera rekordy](#_core_how_a_recordset_constructs_its_sql_statement).

- [Co można zrobić, aby dostosować zaznaczenie](#_core_customizing_the_selection).

Zestawy rekordów wybrać rekordy ze źródła danych za pośrednictwem sterownika ODBC, wysyłając instrukcje SQL do sterownika. Wysłany sql zależy od sposobu projektowania i otwierania klasy pliku recordset.

## <a name="your-options-in-selecting-records"></a><a name="_core_your_options_in_selecting_records"></a>Opcje w wybieraniu rekordów

W poniższej tabeli przedstawiono opcje wyboru rekordów.

### <a name="how-and-when-you-can-affect-a-recordset"></a>Jak i kiedy można wpływać na rekord

|Kiedy|Można|
|--------------|-------------|
|Deklarowanie klasy menedżera rekordów za pomocą kreatora **Dodaj klasę**|Określ, która tabela ma być wybrana.<br /><br /> Określ kolumny, które mają być uwzględniane.<br /><br /> Zobacz [Dodawanie konsumenta odbc MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).|
|Uzupełnij implementację klasy recordset|Zastąpojąć `OnSetOptions` funkcje członkowskie, takie jak (zaawansowane), aby ustawić opcje specyficzne dla aplikacji lub zmienić ustawienia domyślne. Określ elementy członkowskie danych parametrów, jeśli chcesz sparametryzowanego zbioru rekordów.|
|Konstruowanie obiektu aktu `Open`recordset (przed wywołaniem)|Określ warunek wyszukiwania (ewentualnie związek) do użycia w **klauzuli WHERE,** która filtruje rekordy. Zobacz [Recordset: Filtering Records (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).<br /><br /> Określ kolejność sortowania do użycia w **klauzuli ORDER BY,** która sortuje rekordy. Zobacz [Recordset: Sortowanie rekordów (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md).<br /><br /> Określ wartości parametrów dla wszystkich parametrów dodanych do klasy. Zobacz [Recordset: Parametryzacja recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).|

| Uruchamianie kwerendy w ach recordset przez wywołanie `Open`| Określ niestandardowy ciąg SQL, który zastąpi domyślny ciąg SQL skonfigurowany przez kreatora. Zobacz [CRecordset::Otwórz](../../mfc/reference/crecordset-class.md#open) w *odwołaniu do biblioteki klas* i [SQL: Dostosowywanie instrukcji SQL zestawu rekordów (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).|

| Wywołanie `Requery` ponownego zapytania zestawem rekordów z najnowszymi wartościami w źródle danych| Określ nowe parametry, filtr lub sortowanie. Zobacz [Recordset: Requerying a Recordset (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md).|

## <a name="how-a-recordset-constructs-its-sql-statement"></a><a name="_core_how_a_recordset_constructs_its_sql_statement"></a>Jak rekord recordset konstruuje jego SQL Instrukcji

Po wywołaniu funkcji elementu członkowskiego [Open](../../mfc/reference/crecordset-class.md#open) `Open` obiektu zestawienia rekordów tworzy instrukcję SQL przy użyciu niektórych lub wszystkich następujących składników:

- Parametr *lpszSQL* przekazany `Open`do . Jeśli nie null, ten parametr określa niestandardowy ciąg SQL lub część jednego. Struktura analizuje ciąg. Jeśli ciąg jest instrukcja SQL **SELECT** lub INSTRUKCJA **ODBC CALL,** struktura używa ciągu jako instrukcji SQL zestawie rekordów. Jeśli ciąg nie zaczyna się od "SELECT" lub "{CALL", struktura używa tego, co jest dostarczane do konstruowania klauzuli SQL **FROM.**

- Ciąg zwrócony przez [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql). Domyślnie jest to nazwa tabeli określonej dla tablicy rekordów w kreatorze, ale można zmienić sposób zwracany przez tę funkcję. Wywołania `GetDefaultSQL` struktury — jeśli ciąg nie zaczyna się od "SELECT" lub "{CALL", zakłada się, że jest nazwą tabeli, która jest używana do konstruowania ciągu SQL.

- Elementy członkowskie danych pola zestaw rekordów, które mają być powiązane z określonymi kolumnami tabeli. Struktura wiąże kolumny rekordów z adresami tych elementów członkowskich, używając ich jako buforów. Struktura określa korelację elementów członkowskich danych pola z kolumnami tabel z wywołań funkcji [RFX](../../data/odbc/record-field-exchange-using-rfx.md) lub Bulk RFX w funkcji elementu członkowskiego [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) lub [DoBulkFieldExchange.](../../mfc/reference/crecordset-class.md#dofieldexchange)

- [Filtr](../../data/odbc/recordset-filtering-records-odbc.md) dla zbioru rekordów, jeśli istnieje, zawarty w [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) element członkowski danych. Struktura używa tego ciągu do konstruowania klauzuli SQL **WHERE.**

- Kolejność [sortowania](../../data/odbc/recordset-sorting-records-odbc.md) dla zbioru rekordów, jeśli istnieje, zawarte w [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) element członkowski danych. Struktura używa tego ciągu do konstruowania klauzuli **SQL ORDER BY.**

   > [!TIP]
   > Aby użyć klauzuli SQL **GROUP BY** (i ewentualnie klauzuli **HAVING),** należy dołączyć klauzule na końcu ciągu filtru.

- Wartości wszystkich [elementów członkowskich danych parametrów,](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) które określisz dla klasy. Ustawiasz wartości parametrów `Open` tuż `Requery`przed wywołaniem lub . Struktura wiąże wartości parametrów z symbolami zastępczymi "?" w ciągu SQL. W czasie kompilacji należy określić ciąg z symbolami zastępczymi. W czasie wykonywania ramach wypełnia szczegóły na podstawie wartości parametrów, które przekazujesz.

`Open`konstruuje instrukcję SQL **SELECT** z tych składników. Zobacz [dostosowywanie zaznaczenia,](#_core_customizing_the_selection) aby uzyskać szczegółowe informacje o tym, jak struktura używa składników.

Po skonstruowaniu instrukcji, wysyła SQL do Menedżera sterowników ODBC (i biblioteki kursora ODBC, `Open` jeśli jest w pamięci), który wysyła go do sterownika ODBC dla określonego systemu dbms. Sterownik komunikuje się z DBMS do przeprowadzenia wyboru w źródle danych i pobiera pierwszy rekord. Struktura ładuje rekord do elementów członkowskich danych pola zbioru rekordów.

Można użyć kombinacji tych technik, aby otworzyć [tabele](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md) i skonstruować kwerendę na podstawie [sprzężenia](../../data/odbc/recordset-performing-a-join-odbc.md) wielu tabel. Dzięki dodatkowej personalizacji można wywoływać [wstępnie zdefiniowane kwerendy (procedury](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md) przechowywane), wybierać kolumny tabel nieznane w czasie projektowania i [wiązać](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) je z polami zestawów rekordów lub wykonywać większość innych zadań dostępu do danych. Zadania, których nie można wykonać, dostosowując zestawy rekordów, można nadal [wykonywać, wywołując funkcje interfejsu API ODBC](../../data/odbc/odbc-calling-odbc-api-functions-directly.md) lub bezpośrednio wykonując instrukcje SQL za pomocą [CDatabase::ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql).

## <a name="customizing-the-selection"></a><a name="_core_customizing_the_selection"></a>Dostosowywanie zaznaczenia

Oprócz dostarczania filtru, kolejności sortowania lub parametrów, można wykonać następujące działania, aby dostosować wybór zestawu rekordów:

- Przekaż niestandardowy ciąg SQL w *lpszSQL* po wywołaniu [Otwórz](../../mfc/reference/crecordset-class.md#open) dla pliku recordset. Wszystko, co przekażesz w *lpsqSQL* ma pierwszeństwo przed tym, co zwraca funkcję elementu członkowskiego [GetDefaultSQL.](../../mfc/reference/crecordset-class.md#getdefaultsql)

   Aby uzyskać więcej informacji, zobacz [SQL: Dostosowywanie instrukcji SQL (ODBC) (Sql Statement) (ODBC) (The Recordset),](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)która opisuje typy instrukcji SQL (lub częściowe instrukcje), do `Open` których można przekazać, oraz co robi z nimi struktura.

    > [!NOTE]
    >  Jeśli niestandardowy ciąg, który przekazujesz, nie zaczyna się od "SELECT" lub "{CALL", MFC zakłada, że zawiera nazwę tabeli. Dotyczy to również następnego elementu punktowanego.

- Zmień ciąg, który kreator zapisuje w `GetDefaultSQL` funkcji elementu członkowskiego pliku recordset. Edytuj kod funkcji, aby zmienić to, co zwraca. Domyślnie kreator zapisuje `GetDefaultSQL` funkcję zwracaną nazwę pojedynczej tabeli.

   Możesz zwrócić `GetDefaultSQL` dowolny z elementów, które można przekazać w parametrze `Open` *lpszSQL* do . Jeśli nie przekażesz niestandardowego ciągu SQL w *lpszSQL,* struktura używa zwracanego ciągu. `GetDefaultSQL` Co najmniej `GetDefaultSQL` musi zwrócić nazwę pojedynczej tabeli. Ale można go zwrócić wiele nazw tabel, pełną instrukcję **SELECT,** instrukcja ODBC **CALL** i tak dalej. Aby uzyskać listę tego, co można przekazać do *lpszSQL* — lub wrócić `GetDefaultSQL` — zobacz [SQL: Dostosowywanie instrukcji SQL (ODBC) programu Recordset.](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)

   Jeśli wykonujesz sprzężenie dwóch lub `GetDefaultSQL` więcej tabel, przepisz, aby dostosować listę tabel używaną w klauzuli SQL **FROM.** Aby uzyskać więcej informacji, zobacz [Recordset: Performing a Join (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).

- Ręcznie powiąż dodatkowe elementy członkowskie danych pola, być może na podstawie informacji o schemacie źródła danych w czasie wykonywania. Elementy członkowskie danych pola można dodać do klasy zestaw rekordów, [RFX](../../data/odbc/record-field-exchange-using-rfx.md) lub bulk RFX, które wywołują dla nich funkcję elementu członkowskiego [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) lub [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) oraz inicjowania elementów członkowskich danych w konstruktorze klasy. Aby uzyskać więcej informacji, zobacz [Zestaw rekordów: Dynamicznie wiążące kolumny danych (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

- Zastąpokaj funkcje `OnSetOptions`elementów członkowskich zestawu rekordów, takie jak , aby ustawić opcje specyficzne dla aplikacji lub zastąpić domyślne.

Jeśli chcesz oprzeć zestaw rekordów na złożonej instrukcji SQL, musisz użyć kombinacji tych technik dostosowywania. Na przykład być może chcesz użyć klauzul SQL i słów kluczowych, które nie są bezpośrednio obsługiwane przez zestawy rekordów lub być może łączysz wiele tabel.

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: jak zestawy rekordów aktualizują rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[Podstawy ODBC](../../data/odbc/odbc-basics.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[Zestaw rekordów: blokowanie rekordów (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
