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
ms.openlocfilehash: 2f1f5ba7da2e2e61de9356b82f51bc9f2ef1cce9
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055544"
---
# <a name="recordset-how-recordsets-select-records-odbc"></a>Zestaw rekordów: jak zestawy rekordów pobierają rekordy (ODBC)

Ten temat dotyczy klas MFC ODBC.

W tym temacie opisano:

- [Roli i opcji wybierania rekordów](#_core_your_options_in_selecting_records).

- [Jak tworzy jego instrukcji SQL zestawu rekordów i wybiera rekordy](#_core_how_a_recordset_constructs_its_sql_statement).

- [Co można zrobić, aby dostosować wybór](#_core_customizing_the_selection).

Zestawy rekordów wybrać rekordy ze źródła danych za pośrednictwem sterownika ODBC, wysyłając instrukcji języka SQL do sterownika. SQL wysyłane zależy od tego, jak projektować i otwórz klasy zestawu rekordów.

##  <a name="_core_your_options_in_selecting_records"></a> Wybieranie rekordów opcji

W poniższej tabeli przedstawiono opcje, wybierając rekordów.

### <a name="how-and-when-you-can-affect-a-recordset"></a>Jak i kiedy może mieć wpływ na zestaw rekordów

|Gdy użytkownik|Można|
|--------------|-------------|
|Deklarowanie klasy zestawu rekordów z **Dodaj klasę** Kreatora|Określ tabeli, która dokonania wyboru z.<br /><br /> Określ kolumny do dołączenia.<br /><br /> Zobacz [Dodawanie użytkownika MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).|
|Wykonać implementacji klasy zestawu rekordów|Zastąpienie elementów członkowskich, takich jak `OnSetOptions` (zaawansowane), aby ustawić opcje specyficzne dla aplikacji lub zmienić ustawienia domyślne. Jeśli chcesz, aby sparametryzowane zestawu rekordów, należy określić elementy członkowskie danych parametru.|
|Konstruowania obiektu zestawu rekordów (przed wywołaniem `Open`)|Określ warunek wyszukiwania (prawdopodobnie złożonego) do użycia w **gdzie** klauzula, która filtruje rekordy. Zobacz [zestaw rekordów: filtrowanie rekordów (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).<br /><br /> Określanie kolejności sortowania do użycia w **ORDER BY** klauzula, która sortuje rekordy. Zobacz [zestaw rekordów: sortowanie rekordów (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md).<br /><br /> Określ wartości parametrów dla wszystkich parametrów, które dodawana do klasy. Zobacz [zestaw rekordów: parametryzacja zestawu rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).|

| Uruchom zapytanie w zestawie rekordów, wywołując `Open`| Określ niestandardowy ciąg SQL, aby zastąpić domyślny ciąg SQL skonfigurowany przez kreatora. Zobacz [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) w *klasy odwołanie do biblioteki* i [SQL: dostosowywanie instrukcji SQL zestawu rekordów (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md). |

| Wywołaj `Requery` do Requery — zestaw rekordów o najnowsze wartości w źródle danych | Określ nowe parametry, filtrowania lub sortowania. Zobacz [zestaw rekordów: ponowne wysyłanie zapytania do zestawu rekordów (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md). |

##  <a name="_core_how_a_recordset_constructs_its_sql_statement"></a> Jak zestaw rekordów tworzy jego instrukcji SQL

Gdy wywołujesz obiektem rekordem [Otwórz](../../mfc/reference/crecordset-class.md#open) funkcja elementu członkowskiego `Open` tworzy instrukcję SQL przy użyciu niektóre lub wszystkie z następujących składników:

- *LpszSQL* parametr przekazany do `Open`. Jeśli nie ma wartość NULL, ten parametr określa niestandardowy ciąg SQL lub należy do jednej. Struktura analizuje ciąg. Jeśli ciąg jest SQL **wybierz** instrukcji lub ODBC **WYWOŁANIA** instrukcji, w ramach używa ciągu jako instrukcji SQL zestawu rekordów. Jeśli ciąg nie rozpoczyna się od "Wybierz" lub "{CALL", środowisko wykorzystuje, co jest dostarczane do konstruowania SQL **FROM** klauzuli.

- Ciąg zwracany przez [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql). Domyślnie jest to nazwa tabeli, którą określono dla zestawu rekordów w kreatorze, ale można zmienić, funkcja zwraca. Struktura wywołuje `GetDefaultSQL` — Jeśli ciąg nie rozpoczyna się od "Wybierz" lub "{CALL", zakłada się, jako nazwę tabeli, który służy do konstruowania ciągu SQL.


- Pole danych elementy członkowskie zestawu rekordów, które mają być powiązane z określonych kolumn w tabeli. Struktura wiąże kolumn rekordu adresy tych członków, używania ich jako buforów. Określa platformę korelację elementy członkowskie danych pola kolumny tabeli z [RFX](../../data/odbc/record-field-exchange-using-rfx.md) lub zbiorcze RFX funkcja wywołuje w zestawie rekordów [dofieldexchange —](../../mfc/reference/crecordset-class.md#dofieldexchange) lub [dobulkfieldexchange — ](../../mfc/reference/crecordset-class.md#dofieldexchange) funkcja elementu członkowskiego.

- [Filtru](../../data/odbc/recordset-filtering-records-odbc.md) dla zestawu rekordów, jeśli istnieje, zawarte w [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) element członkowski danych. Struktura używa tego ciągu do konstruowania SQL **gdzie** klauzuli.

- [Sortowania](../../data/odbc/recordset-sorting-records-odbc.md) order dla zestawu rekordów, jeśli istnieją, zawarty w [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) element członkowski danych. Struktura używa tego ciągu do konstruowania SQL **ORDER BY** klauzuli.


    > [!TIP]
    >  Aby użyć SQL **GROUP BY** klauzuli (i ewentualnie **HAVING** klauzuli), Dodaj klauzul do końca ciągu filtru.

- Wartości dowolnego [elementy członkowskie danych parametru](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) określ dla tej klasy. Ustawianie wartości parametrów, po prostu, przed wywołaniem `Open` lub `Requery`. Struktura powiązania wartości parametrów, aby "?" symbole zastępcze w ciągu SQL. W czasie kompilacji można określić ciąg z symbolami zastępczymi. W czasie wykonywania struktura wypełnia szczegółowe informacje na podstawie wartości parametru, które można przekazać.

`Open` konstruuje SQL **wybierz** instrukcji z tych składników. Zobacz [Dostosowywanie zaznaczenie](#_core_customizing_the_selection) szczegółowe informacje o używaniu składniki w ramach.

Po konstruowanie instrukcji, `Open` wysyła SQL do Menedżera sterowników ODBC (i Biblioteka kursorów ODBC, jeśli znajduje się w pamięci), która wysyła do sterownika ODBC dla określonego systemu DBMS. Sterownik komunikuje się z systemu DBMS przeprowadzenie zaznaczenia w źródle danych i pobiera pierwszy rekord. Struktura ładuje rekord do elementy członkowskie danych pola zestawu rekordów.

Można użyć obu tych technik jednocześnie, aby otworzyć [tabel](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md) i Utwórz zapytanie na podstawie [sprzężenia](../../data/odbc/recordset-performing-a-join-odbc.md) z wielu tabel. Za pomocą dodatkowych dostosowań, można wywołać [wstępnie zdefiniowane zapytania](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md) (procedury składowanej), wybierz tabelę kolumn nie jest znany w czasie projektowania i [powiązać](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) je do pól rekordów lub można wykonywać większości innych dostęp do danych zadania. Zadania nie można wykonać poprzez dostosowanie zestawów rekordów nadal można osiągnąć przez [wywoływanie funkcji ODBC API](../../data/odbc/odbc-calling-odbc-api-functions-directly.md) lub bezpośrednio wykonywania instrukcji SQL z [CDatabase::ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql).

##  <a name="_core_customizing_the_selection"></a> Dostosowywanie zaznaczenie

Oprócz podawania filtru, kolejności sortowania lub parametry, można wykonać następujące czynności, aby dostosować wybór zestawu rekordów:

- Przekaż niestandardowy ciąg SQL w *lpszSQL* podczas wywoływania [Otwórz](../../mfc/reference/crecordset-class.md#open) zestawu rekordów. Cokolwiek przekazanej *lpsqSQL* ma pierwszeństwo przed co [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) funkcja elementu członkowskiego zwraca.

   Aby uzyskać więcej informacji, zobacz [SQL: dostosowywanie Your zestawu rekordów instrukcji SQL (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md), która opisuje typy instrukcji SQL (lub częściowe instrukcje), którą można przekazać do `Open` i struktura jest z nimi.

    > [!NOTE]
    >  Niestandardowy ciąg, który należy przekazać zaczyna się od "Wybierz" lub "{CALL", MFC przyjęto założenie, że zawiera on nazwę tabeli. Dotyczy to również do następnego elementu listy.

- Instrukcja ALTER ciąg, który kreator zapisuje w twoim zestawie rekordów `GetDefaultSQL` funkcja elementu członkowskiego. Edytuj kod funkcji, aby zmienić ją zwraca. Domyślnie kreator zapisuje `GetDefaultSQL` funkcja, która zwraca nazwę pojedynczej tabeli.

   Może mieć `GetDefaultSQL` zwracać dowolne elementy, które można przekazać *lpszSQL* parametr `Open`. Jeśli nie przekażesz niestandardowy ciąg SQL w *lpszSQL*, struktura używa parametrów, `GetDefaultSQL` zwraca. Co najmniej `GetDefaultSQL` musi zwrócić nazwę pojedynczej tabeli. Ale może być zwrócić wiele nazw tabel, pełne **wybierz** instrukcji, ODBC **WYWOŁANIA** instrukcji i tak dalej. Lista co można przekazać do *lpszSQL* — lub `GetDefaultSQL` zwracają — zobacz [SQL: dostosowywanie Your zestawu rekordów instrukcji SQL (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

   Jeśli przeprowadzasz przyłączenia co najmniej dwie tabele ponownego zapisywania `GetDefaultSQL` dostosować listę tabel w SQL używać **FROM** klauzuli. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: wykonywanie Join (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).


- Ręczne powiązanie dodatkowego pola danych elementów członkowskich, być może na podstawie informacji możesz uzyskać dotyczące schematu źródła danych w czasie wykonywania. Dodaj elementy członkowskie danych pola do klasy zestawu rekordów [RFX](../../data/odbc/record-field-exchange-using-rfx.md) lub zbiorcze RFX funkcja wywołuje dla nich [dofieldexchange —](../../mfc/reference/crecordset-class.md#dofieldexchange) lub [dobulkfieldexchange —](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) funkcja elementu członkowskiego i Inicjowanie elementów członkowskich danych w konstruktorze klasy. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: dynamiczne powiązanie danych kolumn (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

- Zastąpienia funkcji elementów członkowskich zestawu rekordów, takich jak `OnSetOptions`, aby ustawić opcje specyficzne dla aplikacji, lub aby przesłonić wartości domyślne.

Jeśli chcesz utworzyć zestaw rekordów na złożonych instrukcji SQL, należy użyć kombinacji tych metod dostosowywania. Na przykład być może chcesz użyć klauzule SQL i słowa kluczowe nie są bezpośrednio obsługiwane przez zestawy rekordów lub prawdopodobnie są dołączania wielu tabel.

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: jak zestawy rekordów aktualizują rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[Podstawy ODBC](../../data/odbc/odbc-basics.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[Zestaw rekordów: blokowanie rekordów (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)