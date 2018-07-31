---
title: 'Wymiana pól rekordów: Jak działa RFX | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- record editing [C++], using RFX
- RFX (ODBC) [C++], updating data in recordsets
- scrolling [C++]
- ODBC [C++], RFX
- data binding [C++], DFX
- scrolling [C++], RFX
- RFX (ODBC) [C++], binding fields and parameters
ms.assetid: e647cacd-62b0-4b80-9e20-b392deca5a88
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3ebc25519b7e53db719211d61b07137a75665968
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2018
ms.locfileid: "39338080"
---
# <a name="record-field-exchange-how-rfx-works"></a>Wymiana pól rekordów: jak działa RFX
W tym temacie opisano proces RFX. Jest to zaawansowany obejmujący tematu:  
  
-   [RFX i zestawu rekordów](#_core_rfx_and_the_recordset)  
  
-   [Proces RFX](#_core_the_record_field_exchange_process)  
  
> [!NOTE]
>  Ten temat dotyczy klasy pochodne `CRecordset` w wierszu zbiorczego, które podczas pobierania nie została zaimplementowana. Jeśli używasz zbiorcze pobieranie z wiersza zbiorcza wymiana pól rekordów (zbiorcze RFX) jest zaimplementowana. Zbiorcze RFX przypomina RFX. Aby poznać różnice, zobacz [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="_core_rfx_and_the_recordset"></a> RFX i zestawu rekordów  
 Obiekty zestawów rekordów pola danych elementów członkowskich, razem wzięte, stanowią buforu edycji, który przechowuje zaznaczonych kolumnach do jednego rekordu. Jeśli zestaw rekordów pierwszym otwarciu, ma odczytywać pierwszy rekord RFX powiązania (kojarzy) każdego wybrać kolumny do adresu odpowiednie pole składowej danych. Gdy zestaw rekordów aktualizuje rekord, RFX wywołuje funkcje interfejsu API ODBC, aby wysłać SQL **aktualizacji** lub **Wstaw** instrukcji do sterownika. RFX używa jej wiedzy elementy członkowskie danych pola w celu określenia kolumn do zapisania.  
  
 Struktura wykonuje kopię zapasową buforu edycji na określonym etapie, dzięki czemu można przywrócić jego zawartość, jeśli to konieczne. Przed dodaniem nowego rekordu i przed rozpoczęciem edycji istniejącego rekordu RFX kopię zapasową buforu edycji. Spowoduje przywrócenie buforu edycji w niektórych przypadkach, na przykład po `Update` następujące wywołanie `AddNew`. Porzuć bufor nowo zmienionego edycji, na przykład przeniesienie do innego rekordu przed wywołaniem nie jest przywracane buforu edycji `Update`.  
  
 Oprócz wymiana danych między źródłem danych i elementy członkowskie danych pola zestawu rekordów, RFX zarządza Parametry wiążące. Po otwarciu zestawu rekordów w kolejności od związane są wszystkie elementy członkowskie danych parametru "?" symbole zastępcze w instrukcji SQL, `CRecordset::Open` konstrukcji. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: parametryzacja zestawu rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
 Klasa zestawu rekordów zastąpieniu obiektu `DoFieldExchange` wykonuje całą pracę przenoszenia danych w obu kierunkach. Takie jak wymiana danych okna dialogowego (DDX) RFX potrzebuje informacji na temat elementów członkowskich danych klasy. Kreator dostarcza niezbędne informacje, pisząc implementacji specyficznych dla zestawu rekordów `DoFieldExchange` , na podstawie pola danych elementu członkowskiego nazwy i typy danych, określ za pomocą kreatora.  
  
##  <a name="_core_the_record_field_exchange_process"></a> Proces wymiany pól rekordu  
 W tej sekcji opisano sekwencję zdarzeń RFX jako obiekt zestawu rekordów jest otwarty, a w miarę dodawania, aktualizowania i usuwania rekordów. Tabela [sekwencji z RFX operacje podczas rekordów otwórz](#_core_sequence_of_rfx_operations_during_recordset_open) i tabeli [sekwencji z RFX operacje podczas przewijania](#_core_sequence_of_rfx_operations_during_scrolling) w tym temacie pokazują proces jako procesy RFX `Move` polecenia w pliku zestaw rekordów i RFX zarządza aktualizacji. Podczas tych procesów [dofieldexchange —](../../mfc/reference/crecordset-class.md#dofieldexchange) jest wywoływana, aby wykonywać wiele różnych operacji. `m_nOperation` Element członkowski danych [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) obiektu określa kolejnej operacji jest wymagane. Może okazać się przydatne do odczytania [zestaw rekordów: jak zestawy rekordów wybierz rekordów (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) i [zestaw rekordów: jak zestawy rekordów uaktualniają rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) przed przeczytaniem tego materiału.  
  
###  <a name="_mfc_rfx.3a_.initial_binding_of_columns_and_parameters"></a> RFX: Początkowej powiązanie kolumn i parametry  
 Występują następujące działania RFX, w poniższej kolejności, gdy zostanie wywołana obiektem rekordem [Otwórz](../../mfc/reference/crecordset-class.md#open) funkcja elementu członkowskiego:  
  
-   Jeśli zestaw rekordów zawiera elementy członkowskie danych parametru, struktura wywołuje `DoFieldExchange` powiązać parametry zastępcze parametru w parametrach instrukcji SQL zestawu rekordów. Dane zależne od typu reprezentacja wartości parametru jest używana dla każdego symbolu zastępczego znalezione w **wybierz** instrukcji. Dzieje się tak, po instrukcji SQL jest gotowa, ale zanim zostanie on wykonany. Aby uzyskać informacji na temat przygotowywania poufności informacji, zobacz `::SQLPrepare` funkcji w ODBC *odwołania programisty*.  
  
-   Struktura wywołuje `DoFieldExchange` po raz drugi, aby powiązać wartości wybranej kolumny odpowiednie elementy członkowskie danych pola w zestawie rekordów. W ten sposób ustanawiany obiekty zestawów rekordów jako bufor edycji zawierająca kolumny pierwszy rekord.  
  
-   Zestaw rekordów wykonuje instrukcję SQL i źródła danych wybiera pierwszy rekord. Kolumny rekordu są ładowane do elementów członkowskich danych pole w zestawie rekordów.  
  
 W poniższej tabeli przedstawiono sekwencję operacji RFX po otwarciu zestawu rekordów.  
  
### <a name="_core_sequence_of_rfx_operations_during_recordset_open"></a> Sekwencja operacji RFX podczas otwierania zestawu rekordów  
  
|Operacja|Operacja dofieldexchange —|Operacja bazy danych/SQL|  
|--------------------|-------------------------------|-----------------------------|  
|1. Otwórz zestaw rekordów.|||  
||2. Tworzenie instrukcji SQL.||  
|||3. Wyślij SQL.|  
||4. Powiąż elementy członkowskie danych parametru.||  
||5. Powiąż elementy członkowskie danych pola kolumn.||  
|||6. ODBC nie przenoszenia i wypełnia je.|  
||7. Napraw dane dla języka C++.||  
  
 Zestawy rekordów Użyj przygotowany wykonywania ODBC firmy, aby zezwolić na szybkie ponowne wysyłanie zapytania przy użyciu tej samej instrukcji SQL. Aby uzyskać więcej informacji na temat wykonywania przygotowany Zobacz ODBC SDK *odwołania programisty* w bibliotece MSDN.  
  
###  <a name="_mfc_rfx.3a_.scrolling"></a> RFX: przewijanie  
 Podczas przewijania z jednego rekordu do innego, struktura wywołuje `DoFieldExchange` zastąpieniu ich odpowiednimi wartościami wcześniej zapisane w elementy członkowskie danych pola z wartościami dla nowego rekordu.  
  
 W poniższej tabeli przedstawiono sekwencję operacji RFX, gdy użytkownik przesuwa się między rekordami.  
  
### <a name="_core_sequence_of_rfx_operations_during_scrolling"></a> Sekwencja operacji RFX podczas przewijania  
  
|Operacja|Operacja dofieldexchange —|Operacja bazy danych/SQL|  
|--------------------|-------------------------------|-----------------------------|  
|1. Wywołaj `MoveNext` lub jednego z innych funkcji przenoszenia.|||  
|||2. ODBC nie przenoszenia i wypełnia je.|  
||3. Napraw dane dla języka C++.||  
  
###  <a name="_mfc_rfx.3a_.adding_new_records_and_editing_existing_records"></a> RFX: Dodawanie nowych rekordów oraz edytowanie istniejących rekordów  
 Po dodaniu nowego rekordu, zestaw rekordów działa jako bufor edycji do zbudowania zawartość nowego rekordu. Podobnie jak w przypadku dodawania rekordów, edytowanie rekordów polega na zmianę wartości elementów członkowskich danych pole w zestawie rekordów. Z perspektywy RFX sekwencja jest:  
  
1.  Wywołania do zestawu rekordów [działają funkcje AddNew](../../mfc/reference/crecordset-class.md#addnew) lub [Edytuj](../../mfc/reference/crecordset-class.md#edit) funkcja elementu członkowskiego powoduje, że RFX do przechowywania bieżącego buforu edycji, dlatego można je później przywrócić.  
  
2.  `AddNew` lub `Edit` przygotowuje pól w buforze edycji, dlatego RFX może wykryć elementy członkowskie danych zmienionego pola.  
  
     Ponieważ nowy rekord nie ma żadnych poprzedniej wartości, aby porównać Zdobywaj wiedzę dzięki, `AddNew` ustawia wartość każdy element członkowski danych pola na wartość PSEUDO_NULL. Później, gdy wywołujesz `Update`, RFX porównuje wartość każdego członka danych o wartości PSEUDO_NULL. Jeśli tak, element członkowski danych został ustawiony. (PSEUDO_NULL nie jest taka sama jak kolumny rekord z wartością true o wartości Null ani nie jest jedną z tych wersji taka sama jak C++ o wartości NULL.)  
  
     W odróżnieniu od `Update` wywołania dla `AddNew`, `Update` wywołania dla `Edit` porównuje zaktualizowane wartości przy użyciu zapisanych wcześniej wartości, a nie przy użyciu PSEUDO_NULL. Różnica jest to, że `AddNew` nie ma żadnych zapisanych wcześniej wartości do porównania.  
  
3.  Bezpośrednio ustawisz wartości elementy członkowskie danych pola, których wartości, którą chcesz edytować, lub czy chcesz wypełnić dla nowego rekordu. Może to obejmować wywołania `SetFieldNull`.  
  
4.  Wywołania do [aktualizacji](../../mfc/reference/crecordset-class.md#update) sprawdza, czy zmienionego pola danych elementów członkowskich, zgodnie z opisem w kroku 2 (zobacz tabelę [sekwencji z RFX operacje podczas przewijania](#_core_sequence_of_rfx_operations_during_scrolling)). Jeśli nie zostały zmienione, `Update` zwraca wartość 0. Jeśli niektóre elementy członkowskie danych pola zostały zmienione, `Update` przygotowuje i wykonuje SQL **Wstaw** instrukcji, która zawiera wartości dla wszystkich zaktualizowanymi polami w rekordzie.  
  
5.  Aby uzyskać `AddNew`, `Update` stwierdza, przez przywrócenie wcześniej przechowywane wartości rekordu, które były aktualne przed `AddNew` wywołania. Aby uzyskać `Edit`, pozostają nowe edytowanych wartości.  
  
 W poniższej tabeli przedstawiono sekwencję operacji RFX podczas dodawania nowego rekordu lub edytować istniejący rekord.  
  
### <a name="sequence-of-rfx-operations-during-addnew-and-edit"></a>Sekwencja operacji RFX podczas działają funkcje AddNew, Edit  
  
|Operacja|Operacja dofieldexchange —|Operacja bazy danych/SQL|  
|--------------------|-------------------------------|-----------------------------|  
|1. Wywołaj `AddNew` lub `Edit`.|||  
||2. Utwórz kopię zapasową buforu edycji.||  
||3. Aby uzyskać `AddNew`, Oznacz elementy członkowskie danych pola jako "czyste" i wartość Null.||  
|4. Przypisz wartości do elementów członkowskich danych pola zestawu rekordów.|||  
|5. Wywołaj `Update`.|||  
||6. Sprawdź, czy zmienione pola.||  
||7. Tworzenie SQL **Wstaw** poufności informacji dotyczące `AddNew` lub **aktualizacji** poufności informacji dotyczące `Edit`.||  
|||8. Wyślij SQL.|  
||9. Aby uzyskać `AddNew`, Przywróć buforu Edytuj zawartość kopii zapasowej. Aby uzyskać `Edit`, jest usunięcie kopii zapasowej.||  
  
### <a name="rfx-deleting-existing-records"></a>RFX: Usuwanie istniejących rekordów  
 Po usunięciu rekordu RFX Ustawia wszystkie pola na wartość NULL, jako przypomnienie, że rekord zostanie usunięty, a następnie należy przenieść, wyłącz ją. Inne informacje sekwencji RFX nie jest konieczne.  
  
## <a name="see-also"></a>Zobacz też  
 [Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md)   
 [Klient MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [Makra, funkcje globalne i zmienne globalne](../../mfc/reference/mfc-macros-and-globals.md)  
 [Klasa CFieldExchange](../../mfc/reference/cfieldexchange-class.md)   
 [CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)