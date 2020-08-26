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
ms.openlocfilehash: 8bc9ba8a143234bec7927c9578a69a95a511bb9f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837791"
---
# <a name="recordset-dynamically-binding-data-columns-odbc"></a>Zestaw rekordów: dynamiczne powiązanie kolumn danych (ODBC)

Ten temat dotyczy klas MFC ODBC.

Zestawy rekordów umożliwiają zarządzanie kolumnami tabeli powiązań określoną w czasie projektowania, ale istnieją przypadki, w których można powiązać kolumny, które były nieznane w czasie projektowania. W tym temacie objaśniono:

- [Jeśli chcesz powiązać kolumny dynamicznie z zestawem rekordów](#_core_when_you_might_bind_columns_dynamically).

- [Sposób dynamicznego powiązania kolumn w czasie wykonywania](#_core_how_to_bind_columns_dynamically).

> [!NOTE]
> Ten temat dotyczy obiektów pochodnych `CRecordset` , w których nie zaimplementowano pobierania wierszy zbiorczych. Opisane techniki zwykle nie są zalecane, jeśli używasz pobierania wierszy zbiorczych. Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [zestaw rekordów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="when-you-might-bind-columns-dynamically"></a><a name="_core_when_you_might_bind_columns_dynamically"></a> Gdy można dynamicznie powiązać kolumny

> [!NOTE]
> Kreator użytkownika ODBC MFC nie jest dostępny w programie Visual Studio 2019 i nowszych. Nadal można utworzyć konsumenta ręcznie.

W czasie projektowania Kreator aplikacji MFC lub [Kreator użytkownika MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) (z **dodawania klasy**) tworzy klasy zestawu rekordów na podstawie znanych tabel i kolumn w źródle danych. Bazy danych mogą się zmieniać, gdy projektujesz je i później, gdy aplikacja korzysta z tych tabel i kolumn w czasie wykonywania. Ty lub inny użytkownik może dodać lub usunąć tabelę albo dodać lub upuścić kolumny z tabeli, na której opiera się zestaw rekordów aplikacji. Prawdopodobnie nie jest to problem dotyczący wszystkich aplikacji do uzyskiwania dostępu do danych, ale jeśli jest to dla Ciebie, jak można się zaradzić ze zmianami w schemacie bazy danych, innym niż poprzez przeprojektowanie i ponowne skompilowanie? Celem tego tematu jest udzielenie odpowiedzi na to pytanie.

W tym temacie opisano najbardziej typowe przypadki, w których można powiązać kolumny dynamicznie — po rozpoczęciu pracy z zestawem rekordów na podstawie znanego schematu bazy danych, aby obsługiwać dodatkowe kolumny w czasie wykonywania. W tym temacie założono, że dodatkowe kolumny są mapowane na `CString` elementy członkowskie danych pól, najbardziej typowym przypadkiem, chociaż sugestie są dostarczane w celu ułatwienia zarządzania innymi typami danych.

Za pomocą niewielkiej ilości dodatkowego kodu można:

- [Określ, które kolumny są dostępne w czasie wykonywania](#_core_how_to_bind_columns_dynamically).

- [Dynamicznie Powiąż dodatkowe kolumny z zestawem rekordów w czasie wykonywania](#_core_adding_the_columns).

Zestaw rekordów nadal zawiera elementy członkowskie danych dla kolumn, które znasz w czasie projektowania. Zawiera również niewielką ilość dodatkowego kodu, która dynamicznie Określa, czy wszystkie nowe kolumny zostały dodane do tabeli docelowej, a jeśli tak, wiążą te nowe kolumny z dynamicznie przydzielonym magazynem (a nie z elementami członkowskimi danych zestawu rekordów).

Ten temat nie obejmuje innych przypadków powiązań dynamicznych, takich jak usunięte tabele lub kolumny. W takich przypadkach należy bezpośrednio używać wywołań interfejsu API ODBC. Aby uzyskać więcej informacji, zobacz informacje o programie [ODBC Programmer's Reference](/sql/odbc/reference/odbc-programmer-s-reference).

## <a name="how-to-bind-columns-dynamically"></a><a name="_core_how_to_bind_columns_dynamically"></a> Jak dynamicznie powiązać kolumny

Aby dynamicznie powiązać kolumny, należy znać (lub można określić) nazw dodatkowych kolumn. Należy również przydzielić magazyn dla dodatkowych elementów członkowskich danych pól, określić ich nazwy i ich typy oraz określić liczbę dodawanych kolumn.

W poniższej dyskusji przedstawiono dwa różne zestawy rekordów. Pierwszy jest głównym zestawem rekordów, który wybiera rekordy z tabeli docelowej. Drugi to specjalny zestaw rekordów kolumn używany do uzyskiwania informacji o kolumnach w tabeli docelowej.

### <a name="general-process"></a><a name="_core_the_general_process"></a> Proces ogólny

Na najbardziej ogólnym poziomie należy wykonać następujące czynności:

1. Konstruowanie głównego obiektu zestawu rekordów.

   Opcjonalnie możesz przekazać wskaźnik do otwartego `CDatabase` obiektu lub można dostarczyć informacje o połączeniu do zestawu rekordów kolumn w inny sposób.

1. Wykonaj kroki, aby dynamicznie dodać kolumny.

   Zobacz proces opisany w temacie Dodawanie poniższych kolumn.

1. Otwórz główny zestaw rekordów.

   Zestaw rekordów wybiera rekordy i używa wymiany pól rekordów (RFX), aby powiązać kolumny statyczne (te, które są zamapowane na elementy członkowskie danych pola zestawu rekordów) i kolumny dynamiczne (mapowane na dodatkowe miejsce do alokacji).

### <a name="adding-the-columns"></a><a name="_core_adding_the_columns"></a> Dodawanie kolumn

Dynamiczne powiązanie dodanych kolumn w czasie wykonywania wymaga wykonania następujących czynności:

1. Określ w czasie wykonywania kolumny, które znajdują się w tabeli docelowej. Wyodrębnij z tych informacji listę kolumn, które zostały dodane do tabeli od momentu zaprojektowana Klasa zestawu rekordów.

   Dobrym rozwiązaniem jest użycie klasy zestawu rekordów kolumn zaprojektowanej do wysyłania zapytań do źródła danych w celu uzyskania informacji o kolumnach dla tabeli docelowej (takich jak nazwa kolumny i typ danych).

1. Podaj magazyn dla nowych elementów członkowskich danych pola. Ponieważ główna Klasa zestawu rekordów nie ma elementów członkowskich danych pól dla nieznanych kolumn, należy podać miejsce do przechowywania nazw, wartości wyniku i prawdopodobnie informacji o typach danych (Jeśli kolumny są różne typy danych).

   Jednym z metod jest utworzenie co najmniej jednej listy dynamicznej, jedną dla nowych kolumn, drugą dla ich wartości wynikowych i trzecią dla ich typów danych (w razie potrzeby). Te listy, w szczególności lista wartości, zawierają informacje i wymagane miejsce do powiązania. Poniższy rysunek ilustruje Kompilowanie list.

   ![Dynamiczne tworzenie list kolumn do powiązania](../../data/odbc/media/vc37w61.gif "Dynamiczne tworzenie list kolumn do powiązania")<br/>
   Dynamiczne tworzenie list kolumn do powiązania

1. Dodaj wywołanie funkcji RFX w głównej funkcji zestawu rekordów `DoFieldExchange` dla każdej dodanej kolumny. Te wywołania RFX wykonują zadania pobierania rekordu, włącznie z dodatkowymi kolumnami i powiązywanie kolumn z członkami danych zestawu rekordów lub do pamięci masowej dostarczonej dynamicznie.

   Jednym z metod jest dodanie pętli do funkcji głównego zestawu rekordów `DoFieldExchange` , która powoduje pętlę przez listę nowych kolumn, wywołując odpowiednią funkcję RFX dla każdej kolumny na liście. Dla każdego wywołania RFX przekaż nazwę kolumny z listy Nazwa kolumny i lokalizację magazynu w odpowiadającym członku listy wartości wynik.

### <a name="lists-of-columns"></a><a name="_core_lists_of_columns"></a> Listy kolumn

Cztery listy, z którymi należy się skontaktować, przedstawiono w poniższej tabeli.

| Lista | Opis |
|--|--|
| **Bieżąca tabela — kolumny** | (Lista 1 na ilustracji) Lista kolumn znajdujących się obecnie w tabeli w źródle danych. Ta lista może być zgodna z listą kolumn, które są obecnie powiązane z zestawem rekordów. |
| **Powiązane-zestaw rekordów — kolumny** | (Lista 2 na ilustracji) Lista kolumn powiązanych z zestawem rekordów. Te kolumny zawierają już instrukcje RFX w `DoFieldExchange` funkcji. |
| **Kolumny do powiązania — dynamicznie** | (Lista 3 na ilustracji) Lista kolumn w tabeli, ale nie w zestawie rekordów. Oto kolumny, które chcesz powiązać dynamicznie. |
| **Dynamiczne wartości kolumn** | (Lista 4 na ilustracji) Lista zawierająca magazyn dla wartości pobranych z kolumn, które są powiązane dynamicznie. Elementy tej listy odnoszą się do tych w kolumnach do powiązania — dynamicznie, jeden-do-jednego. |

### <a name="building-your-lists"></a><a name="_core_building_your_lists"></a> Kompilowanie list

Z myślą o ogólnej strategii można włączyć szczegóły. Procedury w pozostałej części tego tematu pokazują, jak tworzyć listy wyświetlane na [listach kolumn](#_core_lists_of_columns). Procedury te przeprowadzą Cię przez:

- [Określanie nazw kolumn, które nie są w zestawie rekordów](#_core_determining_which_table_columns_are_not_in_your_recordset).

- [Dostarczanie dynamicznego magazynu dla kolumn dodawanych do tabeli](#_core_providing_storage_for_the_new_columns).

- [Dynamiczne dodawanie wywołań RFX dla nowych kolumn](#_core_adding_rfx_calls_to_bind_the_columns).

### <a name="determining-which-table-columns-are-not-in-your-recordset"></a><a name="_core_determining_which_table_columns_are_not_in_your_recordset"></a> Określanie, które kolumny tabeli nie znajdują się w zestawie rekordów

Utwórz listę (powiązane-zestaw rekordów-kolumn, jak w liście 2 na ilustracji) zawierającej listę kolumn, które są już powiązane z głównym zestawem rekordów. Następnie utwórz listę (kolumny do powiązania — dynamicznie), pochodzącą z kolumn bieżąca tabela i powiązane z zestawem rekordów kolumn), które zawierają nazwy kolumn, które znajdują się w tabeli w źródle danych, ale nie w głównym zestawie rekordów.

##### <a name="to-determine-the-names-of-columns-not-in-the-recordset-columns-to-bind-dynamically"></a>Aby określić nazwy kolumn, które nie są w zestawie rekordów (kolumny do powiązania — dynamicznie)

1. Utwórz listę (powiązane-zestaw rekordów kolumn) kolumn, które są już powiązane w głównym zestawie rekordów.

   Jednym z metod jest utworzenie kolumn powiązanych rekordów w czasie projektowania. Możesz wizualnie przejrzeć wywołania funkcji RFX w funkcji zestawu rekordów, `DoFieldExchange` Aby uzyskać te nazwy. Następnie skonfiguruj listę jako tablicę zainicjowaną z nazwami.

   Na przykład ilustracja przedstawia powiązane z zestawem rekordów kolumny (lista 2) z trzema elementami. W powiązanym zestawie rekordów nie ma kolumny telefonu pokazanej w kolumnach Current-Table (lista 1).

1. Porównywanie kolumn z kolumnami i kolumną powiązanych rekordów w celu utworzenia listy (kolumny do powiązania-dynamicznie) kolumn, które nie są już powiązane w głównym zestawie rekordów.

   Jednym z metod jest przepętlenie listy kolumn w tabeli w czasie wykonywania (kolumny z bieżącą tabelą) i listy kolumn, które są już powiązane w zestawie rekordów (powiązane-zestaw rekordów) równolegle. Na kolumny do powiązania — dynamicznie umieszczaj wszystkie nazwy w kolumnach z bieżącą tabelą, które nie są wyświetlane w powiązanych z zestawami rekordów kolumn.

   Na przykład ilustracja przedstawia kolumny do powiązania — dynamicznie (lista 3) z jednym elementem: kolumna telefonu znaleziona w kolumnach Current-Table-Columns (lista 1), ale nie w powiązanej z zestawami rekordów (lista 2).

1. Utwórz listę wartości z kolumną dynamiczną (jak na liście 4 na ilustracji), w której mają być przechowywane wartości danych odpowiadające każdej nazwie kolumny przechowywanej na liście kolumn do powiązania dynamicznego (kolumny do powiązania — dynamicznie).

   Elementy tej listy odgrywają rolę nowych elementów członkowskich danych pola zestawu rekordów. Są to lokalizacje przechowywania, do których są powiązane kolumny dynamiczne. Opisy list znajdują się w temacie [listy kolumn](#_core_lists_of_columns).

### <a name="providing-storage-for-the-new-columns"></a><a name="_core_providing_storage_for_the_new_columns"></a> Dostarczanie magazynu dla nowych kolumn

Następnie skonfiguruj lokalizacje magazynu dla kolumn, które mają być powiązane dynamicznie. Pomysłem jest udostępnienie elementu listy, w którym będą przechowywane wartości każdej kolumny. Te lokalizacje magazynu są równoległe do zmiennych składowych zestawu rekordów, które przechowują zwykle powiązane kolumny.

#### <a name="to-provide-dynamic-storage-for-new-columns-dynamic-column-values"></a>Aby zapewnić dynamiczny magazyn dla nowych kolumn (wartości dynamiczne kolumn)

1. Kompiluj dynamiczne wartości kolumn, równolegle z kolumnami do powiązania — dynamicznie, aby zawierały wartość danych w każdej kolumnie.

   Na przykład na ilustracji przedstawiono dynamiczne wartości kolumn (lista 4) z jednym elementem: `CString` obiekt zawierający rzeczywisty numer telefonu dla bieżącego rekordu: "555-1212".

   W najbardziej typowym przypadku, dynamiczne wartości kolumn są elementami typu `CString` . W przypadku pracy z kolumnami o różnych typach danych potrzebna jest lista, która może zawierać elementy różnych typów.

Wynikiem powyższych procedur jest dwie główne listy: kolumny do powiązania — dynamicznie zawierające nazwy kolumn i wartości dynamiczne kolumn zawierające wartości w kolumnach dla bieżącego rekordu.

> [!TIP]
> Jeśli nowe kolumny nie są tego samego typu danych, można chcieć utworzyć dodatkową równoległą listę zawierającą elementy, które w jakiś sposób definiują typ każdego odpowiadającego elementu na liście kolumn. (W razie potrzeby można użyć wartości AFX_RFX_BOOL, AFX_RFX_BYTE i tak dalej. Te stałe są zdefiniowane w AFXDB. H.) wybierz typ listy na podstawie sposobu reprezentowania typów danych kolumny.

### <a name="adding-rfx-calls-to-bind-the-columns"></a><a name="_core_adding_rfx_calls_to_bind_the_columns"></a> Dodawanie wywołań RFX w celu powiązania kolumn

Na koniec należy rozmieścić dynamiczne powiązanie, umieszczając wywołania RFX dla nowych kolumn w `DoFieldExchange` funkcji.

##### <a name="to-dynamically-add-rfx-calls-for-new-columns"></a>Aby dynamicznie dodać wywołania RFX dla nowych kolumn

1. W `DoFieldExchange` funkcji składowej głównego zestawu rekordów Dodaj kod, który przechodzi przez listę nowych kolumn (kolumny do powiązania — dynamicznie). W każdej pętli Wyodrębnij nazwę kolumny z kolumn do powiązania-dynamicznie i wartość wynikową dla kolumny z wartości kolumn dynamicznych. Przekaż te elementy do wywołania funkcji RFX odpowiednie dla typu danych kolumny. Opisy list znajdują się w temacie [listy kolumn](#_core_lists_of_columns).

W typowym przypadku, w `RFX_Text` funkcji wywołuje wyodrębnianie `CString` obiektów z list, tak jak w następujących wierszach kodu, w przypadku których kolumny i powiązania są dynamicznie `CStringList` wywoływane, `m_listName` a wartości kolumny dynamiczne są `CStringList` wywoływane `m_listValue` :

```cpp
RFX_Text( pFX,
            m_listName.GetNext( posName ),
            m_listValue.GetNext( posValue ));
```

Aby uzyskać więcej informacji o funkcjach RFX, zobacz [MACROS and Globals](../../mfc/reference/mfc-macros-and-globals.md) w *bibliotece klas Reference*.

> [!TIP]
> Jeśli nowe kolumny mają różne typy danych, użyj instrukcji switch w pętli, aby wywołać odpowiednią funkcję RFX dla każdego typu.

Gdy struktura wywołuje `DoFieldExchange` `Open` proces w celu powiązania kolumn z zestawem rekordów, RFX wywołań kolumn statycznych wiążą się z tymi kolumnami. Następnie pętla wielokrotnie wywołuje funkcje RFX dla kolumn dynamicznych.

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: Praca z dużymi elementami danych (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)
