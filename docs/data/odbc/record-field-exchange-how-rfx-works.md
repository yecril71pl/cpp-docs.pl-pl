---
title: "Wymiana pól rekordów: Jak działa RFX | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- record editing [C++], using RFX
- RFX (ODBC) [C++], updating data in recordsets
- scrolling [C++]
- ODBC [C++], RFX
- data binding [C++], DFX
- scrolling [C++], RFX
- RFX (ODBC) [C++], binding fields and parameters
ms.assetid: e647cacd-62b0-4b80-9e20-b392deca5a88
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 08372f43e87ed17bd8d0c905d40a8d2c289df966
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="record-field-exchange-how-rfx-works"></a>Wymiana pól rekordów: jak działa RFX
W tym temacie opisano proces RFX. Jest to zaawansowane obejmujący tematu:  
  
-   [RFX i zestawu rekordów](#_core_rfx_and_the_recordset)  
  
-   [Proces RFX](#_core_the_record_field_exchange_process)  
  
> [!NOTE]
>  Ten temat dotyczy klasy pochodzące od `CRecordset` w wiersz, który zbiorczego pobierania nie została zaimplementowana. Jeśli używasz zbiorcze pobieranie z wiersza zbiorcza wymiana pól rekordów (RFX zbiorczego) jest zaimplementowana. Zbiorcze RFX jest podobny do RFX. Aby poznać różnice, zobacz [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="_core_rfx_and_the_recordset"></a>RFX i zestawu rekordów  
 Obiekty zestawów rekordów elementy członkowskie danych pola, razem, stanowią edycji buforu, który przechowuje wybranych kolumn jeden rekord. Zestaw rekordów najpierw jest otwarty i ma odczytywać pierwszy rekord, RFX wiązania (stowarzyszonych) każdego zaznaczone kolumny adres elementu członkowskiego danych w odpowiednim polu. W przypadku zestawu rekordów zaktualizowania rekordu, RFX wywołuje funkcje interfejsu API ODBC do wysyłania SQL **aktualizacji** lub **Wstaw** instrukcji do sterownika. RFX używa jej wiedzy elementy członkowskie danych pola do określania kolumn do zapisu.  
  
 Platformę kopię zapasową buforu edycji niektórych etapami, można przywrócić jego zawartość, jeśli to konieczne. Przed dodaniem nowego rekordu i przed rozpoczęciem edycji istniejącego rekordu RFX kopię zapasową buforu edycji. Go przywraca buforu edycji w niektórych przypadkach, na przykład po **aktualizacji** następujące wywołanie `AddNew`. Porzuć buforu nowo zmienionego edycji, na przykład przeniesienie do innego rekordu przed wywołaniem elementu nie jest przywracane buforu edycji **aktualizacji**.  
  
 Oprócz wymiany danych między źródłem danych i elementy członkowskie danych pola zestawu rekordów, RFX zarządza parametrów wiązania. Po otwarciu zestawu rekordów w celu z powiązanych wszystkie elementy członkowskie danych parametru "?" symbole zastępcze w instrukcji SQL który `CRecordset::Open` konstrukcje. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: parametryzacja zestawu rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
 Klasy rekordów zastąpienie `DoFieldExchange` wykonuje całą pracę przenoszenia danych w obu kierunkach. Podobnie jak wymiana danych okna dialogowego (DDX) RFX potrzebuje informacji o danych elementów członkowskich klasy. Kreator dostarcza niezbędne informacje pisząc implementacja specyficzna dla zestawu rekordów `DoFieldExchange` , na podstawie pola danych elementu członkowskiego nazwy i typy danych, należy określić przy użyciu kreatora.  
  
##  <a name="_core_the_record_field_exchange_process"></a>Proces programu Exchange pola rekordu  
 W tej sekcji opisano sekwencję zdarzeń RFX jako obiekty zestawów rekordów jest otwarty i dodawania, aktualizowania i usuwania rekordów. Tabela [sekwencji z RFX operacje podczas rekordów otwórz](#_core_sequence_of_rfx_operations_during_recordset_open) i tabeli [sekwencji z RFX operacje podczas przewijania](#_core_sequence_of_rfx_operations_during_scrolling) w tym temacie Pokaż procesu jako procesy RFX **Przenieś**polecenia w zestawie rekordów i jak RFX zarządza aktualizacji. Podczas tych procesów [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) jest wywoływana w celu wykonania wielu różnych operacji. **M_nOperation** elementu członkowskiego danych [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) obiektu określa działania, które jest wymagane. Może być przydatne do odczytu [zestaw rekordów: jak zestawy rekordów wybierz rekordów (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) i [zestaw rekordów: jak zestawy rekordów aktualizacji rekordów (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) przed przeczytaniem tego materiału.  
  
###  <a name="_mfc_rfx.3a_.initial_binding_of_columns_and_parameters"></a>RFX: Początkowej powiązanie kolumn i parametrów  
 Występują następujące działania RFX, w kolejności przedstawionej podczas wywoływania obiektu zestawu rekordów [Otwórz](../../mfc/reference/crecordset-class.md#open) funkcji członkowskiej:  
  
-   Jeśli zestaw rekordów zawiera elementy członkowskie danych parametru, struktura wywołuje `DoFieldExchange` powiązać parametry zastępcze parametru w ciągu instrukcji SQL zestawu rekordów. Znaleziono dane, zależne od typu reprezentację wartość parametru jest używana dla każdego symbolu zastępczego w **wybierz** instrukcji. Dzieje się tak, gdy instrukcja SQL jest przygotowane, ale przed jego wykonaniem. Aby uzyskać informacji na temat przygotowywania instrukcji, zobacz **:: SQLPrepare** funkcji w ODBC *Podręcznik programisty*.  
  
-   Wywołania framework `DoFieldExchange` po raz drugi powiązać wartości zaznaczonych kolumn odpowiednie elementy członkowskie danych pola w zestawie rekordów. W ten sposób ustanawiany obiekty zestawów rekordów jako bufor edycji zawierająca kolumny pierwszy rekord.  
  
-   Zestaw rekordów wykonuje instrukcję SQL i źródła danych wybiera pierwszy rekord. Rekord kolumn są ładowane do elementy członkowskie danych pola w zestawie rekordów.  
  
 W poniższej tabeli przedstawiono sekwencję operacji RFX po otwarciu zestawu rekordów.  
  
### <a name="_core_sequence_of_rfx_operations_during_recordset_open"></a>Sekwencja operacji RFX podczas otwierania zestawu rekordów  
  
|Operacja|DoFieldExchange operacji|Operacja bazy danych/SQL|  
|--------------------|-------------------------------|-----------------------------|  
|1. Otwórz zestaw rekordów.|||  
||2. Tworzenie instrukcji SQL.||  
|||3. Wyślij SQL.|  
||4. Powiąż elementy członkowskie danych parametru.||  
||5. Elementy członkowskie danych pola można powiązać kolumny.||  
|||6. ODBC nie przeniesienie i wypełnia danych.|  
||7. Napraw dane dla języka C++.||  
  
 Zestawy rekordów umożliwia wykonanie przygotowane przez ODBC umożliwiają szybkie ponowne wysyłanie zapytania o tej samej instrukcji SQL. Aby uzyskać więcej informacji o przygotowanej wykonywania, zobacz ODBC SDK *Podręcznik programisty* w bibliotece MSDN.  
  
###  <a name="_mfc_rfx.3a_.scrolling"></a>RFX: przewijanie  
 Podczas przewijania z jednego rekordu do innego, struktura wywołuje `DoFieldExchange` zamienić wartości wcześniej są przechowywane w elementy członkowskie danych pola z wartościami w nowym rekordzie.  
  
 W poniższej tabeli przedstawiono sekwencję operacji RFX, gdy użytkownik przesuwa się między rekordami.  
  
### <a name="_core_sequence_of_rfx_operations_during_scrolling"></a>Sekwencja operacji RFX podczas przewijania  
  
|Operacja|DoFieldExchange operacji|Operacja bazy danych/SQL|  
|--------------------|-------------------------------|-----------------------------|  
|1. Wywołanie `MoveNext` lub jednego z innych funkcji przenoszenia.|||  
|||2. ODBC nie przeniesienie i wypełnia danych.|  
||3. Napraw dane dla języka C++.||  
  
###  <a name="_mfc_rfx.3a_.adding_new_records_and_editing_existing_records"></a>RFX: Dodawanie nowych rekordów i edytowanie istniejących rekordów  
 Po dodaniu nowego rekordu zestawu rekordów działa jako bufor edycji do zbudowania zawartość nowego rekordu. Podobnie jak w przypadku dodawania rekordów, edytowanie rekordów obejmuje zmianę wartości elementy członkowskie danych pola w zestawie rekordów. Z perspektywy RFX sekwencji jest następujący:  
  
1.  Wywołania do zestawu rekordów [AddNew](../../mfc/reference/crecordset-class.md#addnew) lub [Edytuj](../../mfc/reference/crecordset-class.md#edit) funkcji członkowskiej powoduje RFX do przechowywania bieżący bufor edycji, więc można go później przywrócić.  
  
2.  `AddNew`lub **Edytuj** przygotowuje pól w buforze edycji dzięki RFX może wykryć elementy członkowskie danych pola zmienione.  
  
     Ponieważ rekord nie zawiera żadnych poprzedniej wartości do porównania nowe, `AddNew` ustawia wartość dla każdego elementu członkowskiego danych pola do **PSEUDO_NULL** wartości. Później, podczas wywoływania **aktualizacji**, RFX porównuje wartość każdego elementu danych z **PSEUDO_NULL** wartości. Jeśli tak, element członkowski danych został ustawiony. (**PSEUDO_NULL** nie jest taka sama jak kolumna rekordu o wartości true wartość Null ani ich jest taka sama jak C++ **NULL**.)  
  
     W odróżnieniu od **aktualizacji** wywołania dla `AddNew`, **aktualizacji** wywołania dla **Edytuj** porównuje zaktualizowane wartości przy użyciu zapisanych wcześniej wartości niż przy użyciu **PSEUDO_NULL**. Różnica jest to, że `AddNew` nie zawiera żadnych zapisanych wcześniej wartości do porównania.  
  
3.  Wartości, których chcesz edytować, lub czy chcesz wypełnić dla nowego rekordu bezpośrednio ustawić wartości elementy członkowskie danych pola. Mogą to być wywołanie `SetFieldNull`.  
  
4.  Wywołania do [aktualizacji](../../mfc/reference/crecordset-class.md#update) sprawdza, czy elementy członkowskie danych pola zmienione, zgodnie z opisem w kroku 2 (patrz tabela [sekwencji z RFX operacje podczas przewijania](#_core_sequence_of_rfx_operations_during_scrolling)). Jeśli nie zostały zmienione, **aktualizacji** zwraca wartość 0. Jeśli niektóre elementy członkowskie danych pola zostały zmienione, **aktualizacji** przygotowuje i wykonuje SQL **Wstaw** instrukcji, która zawiera wartości dla wszystkich zaktualizowanych pól w rekordzie.  
  
5.  Dla `AddNew`, **aktualizacji** stwierdza, przywracając wcześniej przechowywane wartości rekordu, które były aktualne przed `AddNew` wywołania. Dla **Edytuj**, nowe wartości edytowanych pozostają bez zmian.  
  
 W poniższej tabeli przedstawiono sekwencję operacji RFX podczas dodawania nowego rekordu lub edycji istniejącego rekordu.  
  
### <a name="sequence-of-rfx-operations-during-addnew-and-edit"></a>Sekwencja operacji RFX podczas AddNew i edytowanie  
  
|Operacja|DoFieldExchange operacji|Operacja bazy danych/SQL|  
|--------------------|-------------------------------|-----------------------------|  
|1. Wywołanie `AddNew` lub **Edytuj**.|||  
||2. Utwórz kopię zapasową buforu edycji.||  
||3. Aby uzyskać `AddNew`, Oznacz elementy członkowskie danych pola jako "Wyczyść" i wartości Null.||  
|4. Przypisanie wartości do zestawu rekordów elementy członkowskie danych pola.|||  
|5. Wywołanie **aktualizacji**.|||  
||6. Sprawdź, czy zmienionych pól.||  
||7. Tworzenie SQL **Wstaw** instrukcji dla `AddNew` lub **aktualizacji** instrukcji dla **Edytuj**.||  
|||8. Wyślij SQL.|  
||9. Aby uzyskać `AddNew`, Przywróć buforu Edytuj zawartość kopii zapasowej. Aby uzyskać **Edytuj**, usuwanie kopii zapasowej.||  
  
### <a name="rfx-deleting-existing-records"></a>RFX: Usuwanie istniejące rekordy  
 Podczas usuwania rekordu RFX Ustawia wszystkie pola **NULL** przypomnieniem usunąć rekordu, który należy przenieść, wyłącz ją. Inne informacje sekwencji RFX nie jest konieczne.  
  
## <a name="see-also"></a>Zobacz też  
 [Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md)   
 [Klient MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [Makra, funkcje globalne i zmienne globalne](../../mfc/reference/mfc-macros-and-globals.md)  
 [Klasa CFieldExchange](../../mfc/reference/cfieldexchange-class.md)   
 [CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)