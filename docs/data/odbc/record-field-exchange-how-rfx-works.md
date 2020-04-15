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
ms.openlocfilehash: 903acf4f55fb2708f4998a2babf3f143c895429b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367175"
---
# <a name="record-field-exchange-how-rfx-works"></a>Wymiana pól rekordów: jak działa RFX

W tym temacie wyjaśniono proces RFX. Jest to zaawansowany temat obejmujący:

- [RFX i recordset](#_core_rfx_and_the_recordset)

- [Proces RFX](#_core_the_record_field_exchange_process)

> [!NOTE]
> Ten temat ma zastosowanie do `CRecordset` klas pochodzących z których pobieranie wiersza zbiorczego nie została zaimplementowana. W przypadku pobierania wierszy zbiorczych zaimplementowana jest zbiorcza wymiana pól rekordów (Bulk RFX). Zbiorczy RFX jest podobny do RFX. Aby zrozumieć różnice, zobacz [Recordset: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="rfx-and-the-recordset"></a><a name="_core_rfx_and_the_recordset"></a>RFX i recordset

Elementy członkowskie danych pola obiektu zestaw rekordów, razem wzięte, stanowią bufor edycji, który zawiera wybrane kolumny jednego rekordu. Gdy zestaw rekordów jest otwierany po raz pierwszy i ma zamiar odczytać pierwszy rekord, RFX wiąże (kojarzy) każdą wybraną kolumnę z adresem odpowiedniego elementu członkowskiego danych pola. Gdy zestawie rekordów aktualizuje rekord, RFX wywołuje funkcje interfejsu API ODBC, aby wysłać instrukcję SQL **UPDATE** lub **INSERT** do sterownika. RFX używa swojej wiedzy o elementach członkowskich danych pola, aby określić kolumny do zapisu.

Struktura kopii zapasowej buforu edycji na niektórych etapach, dzięki czemu można przywrócić jego zawartość, jeśli to konieczne. RFX kopii zapasowej buforu edycji przed dodaniem nowego rekordu i przed edycją istniejącego rekordu. Przywraca bufor edycji w niektórych przypadkach, `Update` na `AddNew`przykład po wywołaniu po . Bufor edycji nie zostanie przywrócony, jeśli porzucisz nowo zmieniony bufor edycji, na przykład przechodząc do innego rekordu przed wywołaniem `Update`.

Oprócz wymiany danych między źródłem danych a członkami danych pola zestawu rekordów, RFX zarządza parametrami wiązania. Po otwarciu zestaw rekordów, wszystkie elementy członkowskie danych parametrów są powiązane w `CRecordset::Open` kolejności "?" symbole zastępcze w instrukcji SQL, która tworzy. Aby uzyskać więcej informacji, zobacz [Recordset: Parametrizing a Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

Przesłonięcia klasy recordset `DoFieldExchange` wykonuje całą pracę, przesuwając dane w obu kierunkach. Podobnie jak wymiana danych dialogowych (DDX), RFX potrzebuje informacji o członkach danych twojej klasy. Kreator udostępnia niezbędne informacje, zapisując dla Ciebie `DoFieldExchange` implementację specyficzne dla zestawów rekordów na podstawie nazw elementów członkowskich danych pola i typów danych określonych za pomocą kreatora.

## <a name="record-field-exchange-process"></a><a name="_core_the_record_field_exchange_process"></a>Proces wymiany pól rekordu

W tej sekcji opisano sekwencję zdarzeń RFX jako obiekt akces jest otwarty i podczas dodawania, aktualizowania i usuwania rekordów. Tabela [Sekwencja operacji RFX podczas otwierania pliku Recordset](#_core_sequence_of_rfx_operations_during_recordset_open) i [tabela Sekwencja operacji RFX podczas przewijania](#_core_sequence_of_rfx_operations_during_scrolling) w tym temacie pokazują proces, gdy RFX przetwarza `Move` polecenie w komecie rekordów i jako RFX zarządza aktualizacją. Podczas tych procesów [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) jest wywoływana do wykonywania wielu różnych operacji. Element `m_nOperation` członkowski danych [obiektu CFieldExchange](../../mfc/reference/cfieldexchange-class.md) określa, która operacja jest żądana. Przed przeczytaniem tego materiału warto przeczytać [plik Recordset: How Records Select Records (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) i [Recordset: How Recordsets Update Records (ODBC).](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)

### <a name="rfx-initial-binding-of-columns-and-parameters"></a><a name="_mfc_rfx.3a_.initial_binding_of_columns_and_parameters"></a>RFX: Początkowe powiązanie kolumn i parametrów

Następujące działania RFX występują w podanej kolejności podczas wywoływania funkcji elementu członkowskiego [Open](../../mfc/reference/crecordset-class.md#open) obiektu wstawki:

- Jeśli zestaw rekordów ma elementy członkowskie `DoFieldExchange` danych parametrów, struktura wywołuje powiązanie parametrów z symbolami zastępczymi parametrów w ciągu instrukcji SQL zestawu rekordów. Zależna od typu danych reprezentacja wartości parametru jest używana dla każdego symbolu zastępczego znalezionego w instrukcji **SELECT.** Dzieje się tak po przygotowaniu instrukcji SQL, ale przed jej wykonaniem. Aby uzyskać informacje na `::SQLPrepare` temat przygotowania instrukcji, zobacz funkcję w *referencji programisty*ODBC .

- Struktura wywołuje `DoFieldExchange` po raz drugi powiązać wartości wybranych kolumn do odpowiednich elementów członkowskich danych pola w zestaw rekordów. Spowoduje to ustanowienie obiektu pliku recordset jako buforu edycji zawierającego kolumny pierwszego rekordu.

- Zestaw rekordów wykonuje instrukcję SQL, a źródło danych wybiera pierwszy rekord. Kolumny rekordu są ładowane do elementów członkowskich danych pól zbioru rekordów.

W poniższej tabeli przedstawiono sekwencję operacji RFX po otwarciu pliku recordset.

### <a name="sequence-of-rfx-operations-during-recordset-open"></a><a name="_core_sequence_of_rfx_operations_during_recordset_open"></a>Sekwencja operacji RFX podczas otwierania wytchnienia rekordu

|Operacja|Operacja DoFieldExchange|Operacja bazy danych/SQL|
|--------------------|-------------------------------|-----------------------------|
|1. Otwórz rekord.|||
||2. Tworzenie instrukcji SQL.||
|||3. Wyślij SQL.|
||4. Powiąż elementy członkowskie danych parametrów.||
||5. Powiąż elementy członkowskie pól z kolumnami.||
|||6. ODBC wykonuje ruch i wypełnia dane.|
||7. Napraw dane dla języka C++.||

Recordsets używać odbc przygotowane wykonanie, aby umożliwić szybkie ponownepodawanie zapytania z tej samej instrukcji SQL. Aby uzyskać więcej informacji na temat przygotowanego wykonania, zobacz *odwołanie programisty* SDK ODBC w bibliotece MSDN.

### <a name="rfx-scrolling"></a><a name="_mfc_rfx.3a_.scrolling"></a>RFX: Przewijanie

Podczas przewijania z jednego rekordu do `DoFieldExchange` drugiego, struktura wywołuje zastąpić wartości wcześniej przechowywane w elementów członkowskich danych pola z wartości dla nowego rekordu.

W poniższej tabeli przedstawiono sekwencję operacji RFX, gdy użytkownik przechodzi z rekordu do rekordu.

### <a name="sequence-of-rfx-operations-during-scrolling"></a><a name="_core_sequence_of_rfx_operations_during_scrolling"></a>Sekwencja operacji RFX podczas przewijania

|Operacja|Operacja DoFieldExchange|Operacja bazy danych/SQL|
|--------------------|-------------------------------|-----------------------------|
|1. `MoveNext` Zadzwoń lub jedną z innych funkcji Move.|||
|||2. ODBC wykonuje ruch i wypełnia dane.|
||3. Napraw dane dla języka C++.||

### <a name="rfx-adding-new-records-and-editing-existing-records"></a><a name="_mfc_rfx.3a_.adding_new_records_and_editing_existing_records"></a>RFX: Dodawanie nowych rekordów i edytowanie istniejących rekordów

Po dodaniu nowego rekordu, plan rejestrowania działa jako bufor edycji w celu utworzenia zawartości nowego rekordu. Podobnie jak w dodawaniu rekordów, edytowanie rekordów polega na zmianie wartości elementów członkowskich danych pól zbioru rekordów. Z punktu widzenia RFX sekwencja jest następująca:

1. Wywołanie funkcji [AddNew](../../mfc/reference/crecordset-class.md#addnew) lub [Edit](../../mfc/reference/crecordset-class.md#edit) elementu członkowskiego w akubcie pliku records powoduje, że rfx przechowuje bieżący bufor edycji, dzięki czemu można go później przywrócić.

1. `AddNew`lub `Edit` przygotowuje pola w buforze edycji, dzięki czemu RFX może wykryć zmienione elementy członkowskie danych pola.

   Ponieważ nowy rekord nie ma poprzednich wartości `AddNew` do porównania nowych z, ustawia wartość każdego elementu członkowskiego danych pola na wartość PSEUDO_NULL. Później podczas wywoływania `Update`RFX porównuje wartość każdego elementu członkowskiego danych z wartością PSEUDO_NULL. Jeśli istnieje różnica, element członkowski danych został ustawiony. (PSEUDO_NULL nie jest taka sama jak kolumna rekordu z prawdziwą wartością Null ani nie jest taka sama jak C++ NULL.)

   W `Update` przeciwieństwie `AddNew`do `Update` wezwania, `Edit` wywołanie porównuje zaktualizowane wartości z wcześniej przechowywanymi wartościami, a nie przy użyciu PSEUDO_NULL. Różnica polega `AddNew` na tym, że nie ma wcześniej przechowywanych wartości do porównania.

1. Bezpośrednio ustawiasz wartości elementów członkowskich danych pola, których wartości chcesz edytować lub które mają zostać wypełnione dla nowego rekordu. Może to `SetFieldNull`obejmować wywołanie .

1. Wywołanie [update](../../mfc/reference/crecordset-class.md#update) sprawdza elementy członkowskie zmienionych danych pola, zgodnie z opisem w kroku 2 (zobacz [tabelę Sekwencja operacji RFX podczas przewijania).](#_core_sequence_of_rfx_operations_during_scrolling) Jeśli żadna `Update` nie uległa zmianie, zwraca wartość 0. Jeśli niektóre elementy członkowskie `Update` danych pola uległy zmianie, przygotowuje i wykonuje instrukcję SQL **INSERT** zawierającą wartości dla wszystkich zaktualizowanych pól w rekordzie.

1. For `AddNew` `Update` , kończy się przywróceniem wcześniej zapisanych wartości rekordu, `AddNew` który był aktualny przed wywołaniem. Dla `Edit`, nowe, edytowane wartości pozostają na swoim miejscu.

W poniższej tabeli przedstawiono sekwencję operacji RFX podczas dodawania nowego rekordu lub edytowania istniejącego rekordu.

### <a name="sequence-of-rfx-operations-during-addnew-and-edit"></a>Sekwencja operacji RFX podczas addnew i edit

|Operacja|Operacja DoFieldExchange|Operacja bazy danych/SQL|
|--------------------|-------------------------------|-----------------------------|
|1. `AddNew` Zadzwoń `Edit`lub .|||
||2. Utwórz zapas zapasowego buforu edycji.||
||3. `AddNew`Dla , oznacz elementy danych pola jako "czyste" i Null.||
|4. Przypisz wartości do elementów członkowskich danych pól zestawów rekordów.|||
|5. `Update`Zadzwoń .|||
||6. Sprawdź, czy nie ma zmienionych pól.||
||7. Zbuduj **INSERT** instrukcję `AddNew` SQL INSERT `Edit`dla lub **instrukcja UPDATE** dla .||
|||8. Wyślij SQL.|
||9. `AddNew`Dla , przywrócić bufor edycji do jego kopii zapasowej zawartości. Dla `Edit`, usuń kopię zapasową.||

### <a name="rfx-deleting-existing-records"></a>RFX: Usuwanie istniejących rekordów

Po usunięciu rekordu rfx ustawia wszystkie pola na NULL jako przypomnienie, że rekord jest usuwany i należy go przenieść. Nie potrzebujesz żadnych innych informacji o sekwencji RFX.

## <a name="see-also"></a>Zobacz też

[Wymiana pól rekordu (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[MFC ODBC zużywają](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Makra, funkcje globalne i zmienne globalne](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[Klasa CFieldExchange](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)
