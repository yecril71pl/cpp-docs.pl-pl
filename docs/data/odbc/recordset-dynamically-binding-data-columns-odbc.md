---
title: 'Zestaw rekordów: dynamiczne powiązanie kolumn danych (ODBC)'
ms.date: 05/09/2019
helpviewer_keywords:
- ODBC recordsets [C++], binding columns dynamically
- data binding [C++], recordset columns
- recordsets [C++], binding data
- data binding [C++], columns in recordsets
- columns [C++], binding to recordsets
ms.assetid: bff67254-d953-4ae4-9716-91c348cb840b
ms.openlocfilehash: e26e62b0e8d613c1a09b077e3bf8d01d1eabba66
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367051"
---
# <a name="recordset-dynamically-binding-data-columns-odbc"></a>Zestaw rekordów: dynamiczne powiązanie kolumn danych (ODBC)

Ten temat dotyczy klas MFC ODBC.

Zestawy rekordów zarządzają kolumnami tabeli powiązania, które można określić w czasie projektowania, ale zdążą przypadki, w których można powiązać kolumny, które były nieznane w czasie projektowania. W tym temacie wyjaśniono:

- [Jeśli można powiązać kolumny dynamicznie z akcesem rekordów](#_core_when_you_might_bind_columns_dynamically).

- [Jak powiązać kolumny dynamicznie w czasie wykonywania](#_core_how_to_bind_columns_dynamically).

> [!NOTE]
> Ten temat dotyczy obiektów pochodzących z `CRecordset` których pobieranie wiersza zbiorczego nie zostało zaimplementowane. Techniki opisane zazwyczaj nie są zalecane, jeśli używasz pobierania wiersza zbiorczego. Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [Rekord rekordów: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="when-you-might-bind-columns-dynamically"></a><a name="_core_when_you_might_bind_columns_dynamically"></a>Kiedy kolumny można powiązać dynamicznie

> [!NOTE]
> Kreator konsumenta odbc MFC nie jest dostępny w programie Visual Studio 2019 i nowszych. Nadal można utworzyć konsumenta ręcznie.

W czasie projektowania Kreator aplikacji MFC lub [Kreator konsumencki MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) (z **dodaj klasę)** tworzy klasy zestawów rekordów na podstawie znanych tabel i kolumn w źródle danych. Bazy danych można zmieniać między podczas projektowania ich i później, gdy aplikacja używa tych tabel i kolumn w czasie wykonywania. Użytkownik lub inny użytkownik może dodać lub upuścić tabelę lub dodać lub upuścić kolumny z tabeli, na której opiera się aplika. To prawdopodobnie nie jest problemem dla wszystkich aplikacji dostępu do danych, ale jeśli jest dla Ciebie, jak można poradzić sobie ze zmianami w schemacie bazy danych, inne niż przez przeprojektowanie i ponowne komppilowanie? Celem tego tematu jest udzielenie odpowiedzi na to pytanie.

W tym temacie opisano najbardziej typowy przypadek, w którym kolumny mogą być powiązane dynamicznie — po rozpoczęciu z zestawy rekordów na podstawie znanego schematu bazy danych, chcesz obsługiwać dodatkowe kolumny w czasie wykonywania. W temacie przyjęto również założenie, `CString` że dodatkowe kolumny są mapowane do elementów członkowskich danych pola, najczęściej spotykanym przypadkiem, chociaż sugestie są dostarczane w celu łatwiejszego zarządzania innymi typami danych.

Dzięki niewielkiej ilości dodatkowego kodu możesz:

- [Określ, które kolumny są dostępne w czasie wykonywania](#_core_how_to_bind_columns_dynamically).

- [Powiąż dodatkowe kolumny z aktu rekordów dynamicznie, w czasie wykonywania](#_core_adding_the_columns).

Zestaw rekordów nadal zawiera elementy członkowskie danych dla kolumn, o których wiesz o czasie projektowania. Zawiera również niewielką ilość dodatkowego kodu, który dynamicznie określa, czy nowe kolumny zostały dodane do tabeli docelowej, a jeśli tak, wiąże te nowe kolumny z dynamicznie przydzielonym magazynem (a nie z elementami członkowskich danych zestawów rekordów).

Ten temat nie obejmuje innych przypadków wiązania dynamicznego, takich jak porzucone tabele lub kolumny. W takich przypadkach należy użyć wywołań INTERFEJSU API ODBC bardziej bezpośrednio. Aby uzyskać więcej informacji, zobacz *odwołanie programisty* SDK ODBC na dysku CD biblioteki MSDN.

## <a name="how-to-bind-columns-dynamically"></a><a name="_core_how_to_bind_columns_dynamically"></a>Jak dynamicznie powiązać kolumny

Aby dynamicznie powiązać kolumny, musisz znać (lub być w stanie określić) nazwy dodatkowych kolumn. Należy również przydzielić magazyn dla dodatkowych elementów członkowskich danych pola, określić ich nazwy i ich typy oraz określić liczbę dodanych kolumn.

W poniższej dyskusji wymieniono dwa różne zestawy rekordów. Pierwszy to główny rekord, który wybiera rekordy z tabeli docelowej. Drugi to specjalny rekord kolumny używany do uzyskania informacji o kolumnach w tabeli docelowej.

### <a name="general-process"></a><a name="_core_the_general_process"></a>Proces ogólny

Na najbardziej ogólnym poziomie wykonaj następujące kroki:

1. Skonstruuj główny obiekt pliku recordset.

   Opcjonalnie należy przekazać wskaźnik `CDatabase` do otwartego obiektu lub być w stanie podać informacje o połączeniu do pliku recordset kolumny w inny sposób.

1. Aby dynamicznie dodawać kolumny, należy wykonać kroki.

   Zobacz proces opisany w Dodawanie kolumn poniżej.

1. Otwórz główny rekord.

   Zestaw rekordów wybiera rekordy i używa wymiany pól rekordów (RFX) do powiązania zarówno kolumn statycznych (mapowanych do elementów członkowskich danych pól zestawu rekordów), jak i kolumn dynamicznych (mapowanych na dodatkowy magazyn, które można przydzielić).

### <a name="adding-the-columns"></a><a name="_core_adding_the_columns"></a>Dodawanie kolumn

Dynamicznie wiążące dodane kolumny w czasie wykonywania wymaga następujących kroków:

1. Określ w czasie wykonywania, jakie kolumny znajdują się w tabeli docelowej. Wyodrębnij z tych informacji listę kolumn, które zostały dodane do tabeli od klasy recordset został zaprojektowany.

   Dobrym rozwiązaniem jest użycie klasy zestaw rekordów kolumny przeznaczone do kwerendy źródła danych dla informacji o kolumnie dla tabeli docelowej (takich jak nazwa kolumny i typ danych).

1. Zapewnij magazyn dla nowych elementów członkowskich danych pola. Ponieważ główna klasa zestaw rekordów nie ma elementów członkowskich danych pola dla nieznanych kolumn, należy podać miejsce do przechowywania nazw, wartości wyników i ewentualnie informacji o typie danych (jeśli kolumny są różne typy danych).

   Jednym z podejść jest tworzenie jednej lub więcej list dynamicznych, jeden dla nowych kolumn nazwy, inny dla ich wartości wyników, a trzeci dla ich typów danych (jeśli to konieczne). Wykazy te, w szczególności lista wartości, zawierają informacje i niezbędne przechowywanie do wiązania. Poniższy rysunek ilustruje tworzenie list.

   ![Tworzenie list kolumn do dynamicznego powiązania](../../data/odbc/media/vc37w61.gif "Tworzenie list kolumn do dynamicznego powiązania")<br/>
   Tworzenie list kolumn do dynamicznego wiązania

1. Dodaj wywołanie funkcji RFX w `DoFieldExchange` funkcji głównego pliku recordset dla każdej dodanej kolumny. Te wywołania RFX wykonują pracę pobierania rekordu, w tym dodatkowych kolumn, i powiązania kolumn z elementami członkowskich danych zestawu rekordów lub z dynamicznie dostarczonym magazynem dla nich.

   Jednym z podejść jest dodanie pętli do `DoFieldExchange` funkcji głównego zestawie rekordów, która zapętla się przez listę nowych kolumn, wywołując odpowiednią funkcję RFX dla każdej kolumny na liście. Przy każdym wywołaniu RFX przekaż nazwę kolumny z listy nazw kolumn i lokalizację magazynu w odpowiednim członie listy wartości wyników.

### <a name="lists-of-columns"></a><a name="_core_lists_of_columns"></a>Listy kolumn

Cztery listy, z którymi musisz pracować, są pokazane w poniższej tabeli.

|||
|-|-|
|**Bieżące kolumny tabeli**| (Lista 1 na ilustracji) Lista kolumn aktualnie w tabeli w źródle danych. Ta lista może być zgodna z listą kolumn aktualnie powiązanych w zestawie rekordów.|
|**Bound-Recordset-Kolumny**| (Lista 2 na ilustracji) Lista kolumn powiązanych w zestawie rekordów. Te kolumny mają już instrukcje `DoFieldExchange` RFX w funkcji.|
|**Kolumny do wiązania dynamicznie**| (Lista 3 na ilustracji) Lista kolumn w tabeli, ale nie w zestawie rekordów. Są to kolumny, które chcesz powiązać dynamicznie.|
|**Dynamiczne wartości kolumn**| (Lista 4 na ilustracji) Lista zawierająca magazyn dla wartości pobranych z kolumn, które są wiązane dynamicznie. Elementy tej listy odpowiadają w kolumnach do wiązania dynamicznie, jeden do jednego.|

### <a name="building-your-lists"></a><a name="_core_building_your_lists"></a>Tworzenie list

Mając na uwadze ogólną strategię, możesz zwrócić się do szczegółów. Procedury w pozostałej części tego tematu pokazują, jak utworzyć listy wyświetlane na [listach kolumn](#_core_lists_of_columns). Procedury prowadzą cię przez:

- [Określanie nazw kolumn, które nie znajdują się w pliku recordset](#_core_determining_which_table_columns_are_not_in_your_recordset).

- [Zapewnienie dynamicznego przechowywania kolumn nowo dodanych do tabeli](#_core_providing_storage_for_the_new_columns).

- [Dynamiczne dodawanie wywołań RFX dla nowych kolumn](#_core_adding_rfx_calls_to_bind_the_columns).

### <a name="determining-which-table-columns-are-not-in-your-recordset"></a><a name="_core_determining_which_table_columns_are_not_in_your_recordset"></a>Określanie kolumn tabeli, których nie ma w twoim rekordze

Tworzenie listy (Bound-Recordset-Columns, jak w liście 2 na ilustracji), która zawiera listę kolumn już związanych w głównym zestawie rekordów. Następnie skompiluj listę (Kolumny do powiązania dynamicznie, pochodzące z bieżących kolumn tabeli i bound-Recordset-Columns), która zawiera nazwy kolumn, które znajdują się w tabeli w źródle danych, ale nie w głównym zestawie rekordów.

##### <a name="to-determine-the-names-of-columns-not-in-the-recordset-columns-to-bind-dynamically"></a>Aby określić nazwy kolumn nie w ach (Kolumny-to-Bind-Dynamically)

1. Tworzenie listy (Bound-Recordset-Columns) kolumn już powiązanych w głównym zestawie rekordów.

   Jednym z podejść jest tworzenie Bound-Recordset-Kolumny w czasie projektowania. Można wizualnie sprawdzić wywołania funkcji RFX w `DoFieldExchange` funkcji pliku recordset, aby uzyskać te nazwy. Następnie skonfiguruj listę jako tablicę zainicjowaną z nazwami.

   Na przykład ilustracja przedstawia Bound-Recordset-Kolumny (Lista 2) z trzema elementami. Brak kolumny Bound-Recordset-Columns w kolumnie Telefon wyświetlanej w kolumnach bieżącej tabeli (lista 1).

1. Porównaj bieżące kolumny tabeli i powiązane kolumny rekordów, aby utworzyć listę (Kolumny-do powiązania-dynamicznie) kolumn, które nie są jeszcze powiązane w głównym zestawie rekordów.

   Jednym z podejść jest pętla przez listę kolumn w tabeli w czasie wykonywania (Bieżące kolumny tabeli) i listy kolumn już powiązanych w zestawie rekordów (Bound-Recordset-Columns) równolegle. W kolumnach do powiązania dynamicznie umieścić wszystkie nazwy w bieżącej tabeli kolumn, które nie są wyświetlane w Bound-Recordset-Kolumny.

   Na przykład ilustracja przedstawia kolumny do wiązania dynamicznie (lista 3) z jednym elementem: kolumna Telefon znaleziona w kolumnach bieżącej tabeli (lista 1), ale nie w kolumnach powiązanych recordset (lista 2).

1. Tworzenie listy dynamicznych wartości kolumn (jak w liście 4 na ilustracji), w którym mają być przechowywane wartości danych odpowiadające każdej nazwie kolumny przechowywanej na liście kolumn do dynamicznego powiązania (Kolumny-do powiązania dynamicznie).

   Elementy tej listy odgrywają rolę nowych elementów członkowskich danych pola zestawie rekordów. Są to lokalizacje magazynu, z którymi są powiązane kolumny dynamiczne. Aby uzyskać opisy list, zobacz [Listy kolumn](#_core_lists_of_columns).

### <a name="providing-storage-for-the-new-columns"></a><a name="_core_providing_storage_for_the_new_columns"></a>Zapewnienie magazynu dla nowych kolumn

Następnie skonfiguruj lokalizacje magazynowania dla kolumn, które mają być powiązane dynamicznie. Chodzi o to, aby zapewnić element listy, w którym do przechowywania wartości każdej kolumny. Te lokalizacje magazynu równolegle zmienne elementu członkowskiego pliku recordset, które przechowują normalnie powiązane kolumny.

#### <a name="to-provide-dynamic-storage-for-new-columns-dynamic-column-values"></a>Aby zapewnić dynamiczny magazyn dla nowych kolumn (Dynamiczne wartości kolumn)

1. Tworzenie wartości dynamicznych kolumn, równolegle do kolumn do powiązania dynamicznie, aby zawierać wartość danych w każdej kolumnie.

   Na przykład ilustracja przedstawia dynamiczne wartości kolumn (lista 4) z jednym elementem: obiektem zawierającym `CString` rzeczywisty numer telefonu dla bieżącego rekordu: "555-1212".

   W najczęstszym przypadku dynamiczne wartości kolumn ma `CString`elementy typu . Jeśli masz do czynienia z kolumnami różnych typów danych, potrzebujesz listy, która może zawierać elementy różnych typów.

Wynikiem poprzednich procedur są dwie główne listy: Kolumny-do powiązania-dynamicznie zawierające nazwy kolumn i Dynamiczne wartości kolumn zawierające wartości w kolumnach dla bieżącego rekordu.

> [!TIP]
> Jeśli nowe kolumny nie są wszystkie tego samego typu danych, można chcieć dodatkowej równoległej listy zawierającej elementy, które w jakiś sposób definiują typ każdego odpowiedniego elementu na liście kolumn. (Można użyć wartości AFX_RFX_BOOL, AFX_RFX_BYTE i tak dalej, aby to zrobić, jeśli chcesz. Te stałe są zdefiniowane w AFXDB. H.) Wybierz typ listy na podstawie sposobu reprezentowania typów danych kolumny.

### <a name="adding-rfx-calls-to-bind-the-columns"></a><a name="_core_adding_rfx_calls_to_bind_the_columns"></a>Dodawanie wywołań RFX do powiązania kolumn

Na koniec należy zorganizować dla wiązania dynamicznego występuje przez umieszczenie RFX wywołania nowych kolumn w funkcji. `DoFieldExchange`

##### <a name="to-dynamically-add-rfx-calls-for-new-columns"></a>Aby dynamicznie dodawać wywołania RFX dla nowych kolumn

1. W funkcji członkowskiej `DoFieldExchange` głównego zestawie rekordów dodaj kod, który zapętla się na liście nowych kolumn (Kolumny-do powiązania-dynamicznie). W każdej pętli wyodrębnij nazwę kolumny z kolumn do powiązania dynamicznie i wartość wyniku dla kolumny z wartości dynamicznych kolumn. Przekaż te elementy do wywołania funkcji RFX odpowiednie dla typu danych kolumny. Aby uzyskać opisy list, zobacz [Listy kolumn](#_core_lists_of_columns).

W typowym przypadku `RFX_Text` wywołania funkcji `CString` wyodrębnić obiekty z list, jak w następujących wierszach kodu, gdzie `CStringList` Kolumny-to-Bind-Dynamically jest wywoływane `m_listName` i dynamiczne wartości kolumny jest `CStringList` o nazwie: `m_listValue`

```cpp
RFX_Text( pFX,
            m_listName.GetNext( posName ),
            m_listValue.GetNext( posValue ));
```

Aby uzyskać więcej informacji na temat funkcji RFX, zobacz [Makra i globalne](../../mfc/reference/mfc-macros-and-globals.md) w *odwołaniu do biblioteki klas*.

> [!TIP]
> Jeśli nowe kolumny są różne typy danych, użyj instrukcji switch w pętli, aby wywołać odpowiednią funkcję RFX dla każdego typu.

Gdy struktura `DoFieldExchange` wywołuje `Open` podczas procesu do powiązania kolumn do pliku recordset, RFX wywołuje kolumny statyczne powiązania tych kolumn. Następnie pętla wielokrotnie wywołuje funkcje RFX dla kolumn dynamicznych.

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: praca z dużymi elementami danych (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)
