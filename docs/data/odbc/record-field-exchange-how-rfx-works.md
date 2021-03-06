---
title: 'Wymiana pól rekordów: jak działa RFX'
ms.date: 11/04/2016
helpviewer_keywords:
- record editing [C++], using RFX
- RFX (ODBC) [C++], updating data in recordsets
- scrolling [C++]
- ODBC [C++], RFX
- data binding [C++], DFX
- scrolling [C++], RFX
- RFX (ODBC) [C++], binding fields and parameters
ms.assetid: e647cacd-62b0-4b80-9e20-b392deca5a88
ms.openlocfilehash: 9e717d0f0ce3b8841feee2beb457fee7221fcf69
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2020
ms.locfileid: "86403793"
---
# <a name="record-field-exchange-how-rfx-works"></a>Wymiana pól rekordów: jak działa RFX

W tym temacie opisano proces RFX. Jest to zaawansowany temat obejmujący:

- [RFX i zestaw rekordów](#_core_rfx_and_the_recordset)

- [Proces RFX](#_core_the_record_field_exchange_process)

> [!NOTE]
> Ten temat dotyczy klas pochodnych `CRecordset` , w których nie zaimplementowano pobierania wierszy zbiorczych. W przypadku korzystania z pobierania wierszy zbiorczych zaimplementowano wymianę zbiorczych pól rekordów (bulk RFX). RFX Bulk jest podobna do RFX. Aby zrozumieć różnice, zobacz [zestaw rekordów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="rfx-and-the-recordset"></a><a name="_core_rfx_and_the_recordset"></a>RFX i zestaw rekordów

Elementy członkowskie danych pola obiektu zestawu rekordów, a razem stanowią bufor edycji, który zawiera wybrane kolumny jednego rekordu. Gdy zestaw rekordów jest otwierany i ma odczytać pierwszy rekord, RFX bind (Associates) każdej zaznaczonej kolumny do adresu odpowiedniego elementu członkowskiego danych pola. Gdy zestaw rekordów aktualizuje rekord, RFX wywołuje funkcje interfejsu API ODBC w celu wysłania instrukcji SQL **Update** lub **INSERT** do sterownika. RFX używa swoich informacji o elementach członkowskich danych pól, aby określić kolumny do zapisu.

Platforma tworzy kopię zapasową bufora edycji na określonych etapach, aby można było przywrócić jego zawartość w razie potrzeby. RFX tworzy kopię zapasową buforu edycji przed dodaniem nowego rekordu i przed edytowaniem istniejącego rekordu. Przywraca bufor edycji w niektórych przypadkach, na przykład po `Update` wywołaniu poniżej `AddNew` . Bufor edycji nie zostanie przywrócony, jeśli porzucasz nowo zmieniony bufor edycji przez, na przykład, przechodzenie do innego rekordu przed wywołaniem `Update` .

Oprócz wymiany danych między źródłem danych i elementami członkowskimi danych pola zestawu rekordów RFX zarządza parametrami powiązań. Po otwarciu zestawu rekordów wszystkie elementy członkowskie danych parametrów są powiązane z kolejnością symboli zastępczych "?" w instrukcji SQL, która `CRecordset::Open` konstruuje. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: parametryzacja a zestaw rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

Zastąpienie klasy zestawu rekordów `DoFieldExchange` wykonuje całą prace, przesuwając dane w obu kierunkach. Podobnie jak w wymianie danych okna dialogowego (DDX), RFX potrzebuje informacji o elementach członkowskich danych klasy. Kreator udostępnia niezbędne informacje, pisząc implementację specyficzną dla zestawu rekordów `DoFieldExchange` dla użytkownika, na podstawie nazw elementów członkowskich danych pól i typów danych określonych za pomocą kreatora.

## <a name="record-field-exchange-process"></a><a name="_core_the_record_field_exchange_process"></a>Proces wymiany pola rekordu

W tej sekcji opisano sekwencję zdarzeń RFX, które są otwierane, a w miarę dodawania, aktualizowania i usuwania rekordów. Sekwencja tabeli [operacji RFX podczas otwierania zestawu rekordów](#_core_sequence_of_rfx_operations_during_recordset_open) i [sekwencja tabeli operacji RFX podczas przewijania](#_core_sequence_of_rfx_operations_during_scrolling) w tym temacie przedstawiają proces jako RFX przetwarza `Move` polecenie w zestawie rekordów, a jako RFX zarządza aktualizacją. Podczas tych procesów [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) jest wywoływana w celu wykonywania wielu różnych operacji. `m_nOperation`Element członkowski danych obiektu [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) określa żądaną operację. Pomocne może być odczytanie [zestawu rekordów: jak zestawy rekordów wybierają rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) i [zestaw rekordów: jak zestawy rekordów aktualizują rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) przed odczytaniem tego materiału.

### <a name="rfx-initial-binding-of-columns-and-parameters"></a><a name="_mfc_rfx.3a_.initial_binding_of_columns_and_parameters"></a>RFX: początkowe powiązanie kolumn i parametrów

Następujące działania RFX są wykonywane w pokazanej kolejności, gdy wywoływana jest funkcja [Open](../../mfc/reference/crecordset-class.md#open) member obiektu zestawu rekordów:

- Jeśli zestaw rekordów zawiera elementy członkowskie danych parametrów, struktura wywołuje `DoFieldExchange` powiązania parametrów z symbolami zastępczymi parametrów w ciągu instrukcji SQL zestawu rekordów. Reprezentacja wartości parametru w zależności od typu danych jest używana dla każdego symbolu zastępczego znalezionego w instrukcji **SELECT** . Dzieje się tak po przygotowaniu instrukcji SQL, ale przed jej wykonaniem. Aby uzyskać informacje na temat przygotowania instrukcji, zobacz `::SQLPrepare` funkcję w *Kompendium ODBC programmer's Reference*.

- Platforma wywołuje `DoFieldExchange` drugi raz, aby powiązać wartości wybranych kolumn z odpowiednimi elementami członkowskimi danych pól w zestawie rekordów. Spowoduje to nawiązanie obiektu zestawu rekordów jako buforu edycji zawierającego kolumny pierwszego rekordu.

- Zestaw rekordów wykonuje instrukcję SQL, a źródło danych wybiera pierwszy rekord. Kolumny rekordu są ładowane do elementów członkowskich danych pola zestawu rekordów.

W poniższej tabeli przedstawiono sekwencję operacji RFX podczas otwierania zestawu rekordów.

### <a name="sequence-of-rfx-operations-during-recordset-open"></a><a name="_core_sequence_of_rfx_operations_during_recordset_open"></a>Sekwencja operacji RFX podczas otwierania zestawu rekordów

|Operacja|DoFieldExchange, operacja|Operacja bazy danych/SQL|
|--------------------|-------------------------------|-----------------------------|
|1. Otwórz zestaw rekordów.|||
||2. Utwórz instrukcję języka SQL.||
|||3. Wyślij kod SQL.|
||4. powiązywanie elementów członkowskich danych parametru.||
||5. powiązywanie elementów członkowskich danych pól z kolumnami.||
|||6. ODBC wykonuje przenoszenie i wypełnianie danych.|
||7. napraw dane dla języka C++.||

Zestawy rekordów używają przygotowanego wykonania ODBC, aby umożliwić szybkie przeszukiwanie przy użyciu tej samej instrukcji SQL. Aby uzyskać więcej informacji o przygotowanym wykonaniu, zobacz informacje o programie [ODBC Programmer's Reference](/sql/odbc/reference/odbc-programmer-s-reference).

### <a name="rfx-scrolling"></a><a name="_mfc_rfx.3a_.scrolling"></a>RFX: przewijanie

Podczas przewijania z jednego rekordu do innego, struktura wywołuje `DoFieldExchange` zastępowanie wartości wcześniej przechowywanych w elementach członkowskich danych pól wartościami dla nowego rekordu.

W poniższej tabeli przedstawiono sekwencję operacji RFX, gdy użytkownik przechodzi z rekordu do rekordu.

### <a name="sequence-of-rfx-operations-during-scrolling"></a><a name="_core_sequence_of_rfx_operations_during_scrolling"></a>Sekwencja operacji RFX podczas przewijania

|Operacja|DoFieldExchange, operacja|Operacja bazy danych/SQL|
|--------------------|-------------------------------|-----------------------------|
|1. wywołanie `MoveNext` lub jedna z innych funkcji przenoszenia.|||
|||2. ODBC wykonuje przenoszenie i wypełnianie danych.|
||3. napraw dane dla języka C++.||

### <a name="rfx-adding-new-records-and-editing-existing-records"></a><a name="_mfc_rfx.3a_.adding_new_records_and_editing_existing_records"></a>RFX: Dodawanie nowych rekordów i edytowanie istniejących rekordów

W przypadku dodania nowego rekordu zestaw rekordów działa jako bufor edycji, aby skompilować zawartość nowego rekordu. Podobnie jak w przypadku dodawania rekordów, Edycja rekordów obejmuje zmianę wartości elementów członkowskich danych pola zestawu rekordów. W perspektywie RFX sekwencja jest następująca:

1. Wywołanie metody [AddNew](../../mfc/reference/crecordset-class.md#addnew) lub [Edit](../../mfc/reference/crecordset-class.md#edit) elementu członkowskiego zestawu rekordów powoduje, że RFX do przechowywania bieżącego buforu edycji, aby można go było przywrócić później.

1. `AddNew`lub `Edit` przygotowuje pola w buforze edycji, aby RFX mogli wykryć zmieniony element członkowski danych pola.

   Ponieważ nowy rekord nie ma poprzednich wartości do porównania nowych z, `AddNew` ustawia wartość każdego elementu członkowskiego danych pola na wartość PSEUDO_NULL. Później, po wywołaniu `Update` , RFX porównuje każdą wartość elementu członkowskiego danych z wartością PSEUDO_NULL. Jeśli istnieje różnica, element członkowski danych został ustawiony. (PSEUDO_NULL nie jest taka sama jak kolumna rekordu o prawdziwej wartości null ani nie jest taka sama jak w przypadku języka C++ NULL.)

   W przeciwieństwie `Update` do wywołania `AddNew` , `Update` wywołanie `Edit` porównuje zaktualizowane wartości z wcześniej przechowywanymi wartościami zamiast używać PSEUDO_NULL. Różnica polega na tym, że `AddNew` nie ma wcześniej przechowywanych wartości do porównania.

1. Można bezpośrednio ustawić wartości elementów członkowskich danych pól, których wartości mają być edytowane lub które mają zostać wypełnione dla nowego rekordu. Może to obejmować wywoływanie metody `SetFieldNull` .

1. Twoje wywołanie [aktualizacji](../../mfc/reference/crecordset-class.md#update) sprawdza, czy zmieniono elementy członkowskie danych pola, zgodnie z opisem w kroku 2 (zobacz [sekwencję tabeli operacji RFX podczas przewijania](#_core_sequence_of_rfx_operations_during_scrolling)). Jeśli żaden z nich nie został zmieniony, `Update` zwraca wartość 0. Jeśli niektóre elementy członkowskie danych pola zostały zmienione, program `Update` przygotuje i wykona instrukcję SQL **INSERT** , która zawiera wartości dla wszystkich zaktualizowanych pól w rekordzie.

1. W odniesieniu do `AddNew` , `Update` przywraca poprzednio przechowywane wartości rekordu, który był aktualny przed `AddNew` wywołaniem. Dla `Edit` , nowe edytowane wartości pozostają na miejscu.

W poniższej tabeli przedstawiono sekwencję operacji RFX podczas dodawania nowego rekordu lub edytowania istniejącego rekordu.

### <a name="sequence-of-rfx-operations-during-addnew-and-edit"></a>Sekwencja operacji RFX podczas AddNew i Edit

|Operacja|DoFieldExchange, operacja|Operacja bazy danych/SQL|
|--------------------|-------------------------------|-----------------------------|
|1. wywołanie `AddNew` lub `Edit` .|||
||2. Utwórz kopię zapasową buforu edycji.||
||3. Aby `AddNew` oznaczyć elementy członkowskie danych pola jako "czyste" i null.||
|4. Przypisz wartości do elementów członkowskich danych pola zestawu rekordów.|||
|5. Wywołaj metodę `Update` .|||
||6. Sprawdź, czy zmieniono pola.||
||7. Kompiluj instrukcję **INSERT** języka SQL for `AddNew` lub **Update** dla elementu `Edit` .||
|||8. Wyślij kod SQL.|
||9. w przypadku programu `AddNew` Przywróć zawartość bufora edycji do jego zawartości kopii zapasowej. W przypadku programu `Edit` Usuń kopię zapasową.||

### <a name="rfx-deleting-existing-records"></a>RFX: usuwanie istniejących rekordów

Po usunięciu rekordu RFX ustawia wszystkie pola na NULL jako przypomnienie, że rekord został usunięty i należy go przenieść. Nie są potrzebne żadne inne informacje o sekwencji RFX.

## <a name="see-also"></a>Zobacz też

[Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Korzystanie z MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Makra, funkcje globalne i zmienne globalne](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[Klasa CFieldExchange](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset::D oFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)
