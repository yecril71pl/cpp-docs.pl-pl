---
title: 'Zestaw rekordów: Dynamiczne powiązanie kolumn danych (ODBC) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets [C++], binding columns dynamically
- data binding [C++], recordset columns
- recordsets [C++], binding data
- data binding [C++], columns in recordsets
- columns [C++], binding to recordsets
ms.assetid: bff67254-d953-4ae4-9716-91c348cb840b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fe0be424b07fd9d13eec63c56172b2b0195b83d9
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2018
ms.locfileid: "39338814"
---
# <a name="recordset-dynamically-binding-data-columns-odbc"></a>Zestaw rekordów: dynamiczne powiązanie kolumn danych (ODBC)
Ten temat dotyczy klas MFC ODBC.  
  
 Zestawy rekordów zarządzać kolumn tabeli powiązania, które określisz w czasie projektowania, ale istnieją przypadki, gdy chcesz powiązać kolumny, które były nieznane do Ciebie w czasie projektowania. W tym temacie opisano:  
  
-   [Kiedy warto powiązać kolumny dynamicznie zestawu rekordów](#_core_when_you_might_bind_columns_dynamically).  
  
-   [Jak powiązać kolumny dynamicznie w czasie wykonywania](#_core_how_to_bind_columns_dynamically).  
  
> [!NOTE]
>  Ten temat dotyczy obiektów pochodzących od `CRecordset` w wierszu zbiorczego, które podczas pobierania nie została zaimplementowana. Techniki opisane zazwyczaj nie są zalecane, jeśli używasz zbiorcze pobieranie z wiersza. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="_core_when_you_might_bind_columns_dynamically"></a> Kiedy może powiązać kolumny dynamicznie  
 W czasie projektowania, Kreator aplikacji MFC lub [Kreator użytkownika interfejsu ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) (z **Dodaj klasę**) tworzy klasy zestawu rekordów na podstawie znanych tabel i kolumn w źródle danych. Bazy danych może się zmieniać między podczas projektowania je i nowsze, gdy Twoja aplikacja używa tych tabel i kolumn w czasie wykonywania. Ty lub inny użytkownik może dodać Porzuć tabelę lub dodawanie lub usuwanie kolumn z tabeli, która korzysta z aplikacji w zestawie rekordów. To prawdopodobnie nie jest wymagana dla wszystkich aplikacji dostęp do danych, ale jeśli jest dla Ciebie, jak możesz radzić sobie z zmiany w schemacie bazy danych, innych niż przeprojektowanie i ponownej kompilacji? Ten temat ma na celu odpowiedzieć na to pytanie.  
  
 W tym temacie opisano najbardziej typowe przypadek, w którym może powiązać kolumny dynamicznie — mających uruchomione przy użyciu zestawu rekordów na podstawie schematu bazy danych znane, chcesz obsługiwać dodatkowe kolumny w czasie wykonywania. Dodatkowo tematu założono, mapowania dla dodatkowych kolumn `CString` pola danych elementów członkowskich, najbardziej typowych przypadkach, mimo że sugestie są dostarczane w celu zarządzania innymi typami danych.  
  
 Z małą ilością dodatkowego kodu możesz wykonywać następujące czynności:  
  
-   [Określić, które kolumny są dostępne w czasie wykonywania](#_core_how_to_bind_columns_dynamically).  
  
-   [Należy powiązać dodatkowe kolumny rekordów dynamicznie w czasie wykonywania](#_core_adding_the_columns).  
  
 Rekordów nadal zawiera elementy członkowskie danych dla kolumny, które wiedzieli o w czasie projektowania. On również zawiera niewielką ilość dodatkowego kodu, który dynamicznie Określa, czy wszystkie nowe kolumny zostały dodane do tabeli docelowej i, jeśli tak, powiązanie tych nowych kolumn dynamicznie przydzielonej pamięci masowej (a nie do zestawu rekordów składowych danych).  
  
 Ten temat nie obejmuje innych przypadkach wiązanie dynamiczne, takie jak porzuconych tabele lub kolumny. Dla tych przypadków należy używać wywołań interfejsu API ODBC bardziej bezpośrednio. Aby uzyskać informacje, zobacz zestaw SDK ODBC *odwołania programisty* na dysku CD z biblioteki MSDN.  
  
##  <a name="_core_how_to_bind_columns_dynamically"></a> Instrukcje dynamiczne powiązanie kolumn  
 Aby dynamiczne powiązanie kolumn, musisz znać (lub można określić) nazwy dodatkowe kolumny. Należy również przydzielania pamięci dla dodatkowych pól składowych danych, określ ich nazwy i ich typy i określanie liczby kolumn, które dodajesz.  
  
 Następujące dyskusji wymienia dwa różne zestawy rekordów. Pierwszy jest głównym rekordów, który wybiera rekordy z tabeli docelowej. Drugi to specjalne kolumny zestawu rekordów, używany do uzyskiwania informacji na temat kolumny w tabeli docelowej.  
  
###  <a name="_core_the_general_process"></a> Proces ogólne  
 Najbardziej ogólny poziom, wykonaj następujące kroki:  
  
1.  Skonstruuj obiekt główny zestaw rekordów.  
  
     Opcjonalnie można przekazać wskaźnik do otwartego `CDatabase` obiektu lub podać informacje o połączeniu kolumny zestawu rekordów w inny sposób.  
  
2.  Wykonaj kroki, aby dynamicznie dodać kolumny.  
  
     Zobacz procesu opisanego w Dodawanie kolumn poniżej.  
  
3.  Otwórz okno główne rekordów.  
  
     Zestaw rekordów wybiera rekordów i używa wymiana pól rekordów (RFX), aby powiązać zarówno statyczne kolumn, (te mapowane na elementy członkowskie danych pola rekordów), jak i dynamiczne kolumn (przypisane do dodatkowego magazynu, który przydzielasz).  
  
###  <a name="_core_adding_the_columns"></a> Dodawanie kolumn  
 Dynamiczne powiązanie dodane kolumny w czasie wykonywania wymaga wykonania następujących czynności:  
  
1.  Określ w czasie wykonywania, co to są kolumny w tabeli docelowej. Wyodrębnij dane listy kolumn, które zostały dodane do tabeli, ponieważ klasa zestaw rekordów został zaprojektowany.  
  
     Dobra metoda jest użycie klasy kolumny zestawu rekordów, zaprojektowane, aby zbadać źródło danych, aby uzyskać informacje o kolumnach dla tabeli docelowej (na przykład w kolumnie nazwę i typ danych).  
  
2.  Zapewnianie magazynowania dla nowych elementów członkowskich danych pola. Ponieważ klasa głównego zestawu rekordów nie ma nieznany kolumn, elementy członkowskie danych pola, musisz podać miejsce do przechowywania nazwy, wartości wyników i prawdopodobnie typu danych (Jeśli kolumny są różnych typów danych).  
  
     Jedno z podejść jest kompilacja jedną lub więcej list dynamiczne, jeden dla nazwy nowych kolumn, innej wartości wyników i trzecią ich typów danych (w razie potrzeby). Te listy szczególnie listę wartości, podaj informacje i niezbędne magazynu dla powiązania. Na poniższym rysunku przedstawiono tworzenie listy.  
     ![Tworzenie listy kolumn, które można powiązać dynamicznie](../../data/odbc/media/vc37w61.gif "vc37w61")  
Tworzenie listy kolumn, które można powiązać dynamicznie  
  
3.  Dodaj wywołanie funkcji RFX w głównym zestawie rekordów `DoFieldExchange` funkcji dla poszczególnych dodanych kolumn. Te wywołania RFX wykonują pracę pobieranie rekord, w tym dodatkowe kolumny i powiązania do elementów członkowskich danych zestawu rekordów lub dynamicznie podane magazynu kolumn dla nich.  
  
     Jednym z podejść jest dodawanie pętli do głównego zestawu rekordów `DoFieldExchange` funkcja, która przetwarza listę nowych kolumn, wywołanie odpowiedniej funkcji RFX dla każdej kolumny na liście w pętli. Przy każdym wywołaniu RFX przekazać nazwę kolumny z listy nazwy kolumn i lokalizację magazynu w elemencie członkowskim odpowiednie listy wartości wyników.  
  
###  <a name="_core_lists_of_columns"></a> Listy kolumn  
 W poniższej tabeli przedstawiono cztery listy, które są potrzebne do pracy z.  
  
 **Bieżącej tabeli kolumn (1 listy na ilustracji)** listy kolumn w tabeli w źródle danych. Ta lista może być jest zgodny z listą kolumn, które obecnie powiązany w twoim zestawie rekordów.  
  
 **Powiązane z zestawu rekordów kolumn (2 listy na ilustracji)**  
 Powiązana lista kolumn w twoim zestawie rekordów. Tymi kolumnami już znajdują się instrukcje RFX w swojej `DoFieldExchange` funkcji.  
  
 **Kolumny — do — powiązania-dynamicznie (3 listy na ilustracji)**  
 Lista kolumn w tabeli, ale nie w twoim zestawie rekordów. Są to kolumny, które chcesz powiązać dynamicznie.  
  
 **Dynamiczne kolumny wartości (4 listy na ilustracji)**  
 Lista zawierająca magazynu dla wartości są pobierane z kolumny, które można powiązać dynamicznie. Elementy na tej liście odpowiadają w kolumnach — do — powiązania-dynamicznie, jeden-do-jednego.  
  
###  <a name="_core_building_your_lists"></a> Tworzenie list  
 Z ogólną strategią, pamiętając można włączyć do szczegółów. Procedury opisane w pozostałej części tego tematu dowiesz się, jak tworzyć listy pokazano w [listy kolumn](#_core_lists_of_columns). Procedury przeprowadzą Cię przez proces:  
  
-   [Określanie nazwy kolumn, których nie ma rekordów](#_core_determining_which_table_columns_are_not_in_your_recordset).  
  
-   [Zapewnianie pamięci dynamicznej dla nowo dodane do tabeli kolumny](#_core_providing_storage_for_the_new_columns).  
  
-   [Dynamiczne dodawanie RFX wymaga nowych kolumn](#_core_adding_rfx_calls_to_bind_the_columns).  
  
###  <a name="_core_determining_which_table_columns_are_not_in_your_recordset"></a> Określanie w twoim zestawie rekordów nie mają kolumn tabeli  
 Twórz listę (kolumny powiązane z — zestaw rekordów-, jak lista 2 na ilustracji), która zawiera listę kolumn już powiązane w głównym rekordów. Następnie można utworzyć listy (kolumny — do — powiązania-dynamicznie tworzony na podstawie bieżącej tabeli kolumn i kolumny w przypadku zestawu rekordów powiązanego), która zawiera nazwy kolumn, które są w tabeli w źródle danych, ale nie w głównym rekordów.  
  
##### <a name="to-determine-the-names-of-columns-not-in-the-recordset-columns-to-bind-dynamically"></a>Aby określić nazwy kolumn w zestawie rekordów (kolumn do Bind — dynamicznie)  
  
1.  Tworzenie listy (ruch kolumny powiązane z zestawu rekordów) kolumny już powiązane w głównym rekordów.  
  
     Jedno z podejść jest tworzenie kolumny w przypadku zestawu rekordów powiązanego w czasie projektowania. Możesz wizualnie badać wywołania funkcji RFX w zestawie rekordów `DoFieldExchange` funkcję w celu uzyskania tych nazw. Następnie skonfiguruj listy jako tablicę, zainicjować za pomocą nazwy.  
  
     Na przykład na ilustracji przedstawiono powiązane z zestawu rekordów kolumn (lista 2) za pomocą trzech elementów. Kolumny w przypadku zestawu rekordów powiązanego brakuje kolumny Phone wyświetlane w bieżącej tabeli kolumn (listy 1).  
  
2.  Porównanie bieżącej tabeli kolumn i kolumny w przypadku zestawu rekordów powiązanego do tworzenia listy (kolumn do Bind — dynamiczne) kolumn nie jest jeszcze granicy w głównym rekordów.  
  
     Jedno z podejść jest w czasie wykonywania (ruch kolumny bieżącej tabeli) i listy kolumn, które już powiązane w twoim zestawie rekordów (ruch kolumny powiązane z zestawu rekordów) równolegle w pętli poprzez listy kolumn w tabeli. Do kolumn — do — powiązania-dynamicznie umieść żadnych nazw w bieżącej —-kolumn tabeli, które nie są wyświetlane w kolumnach w przypadku zestawu rekordów powiązanych.  
  
     Na przykład na ilustracji przedstawiono kolumn do Bind — dynamicznie (listy 3) z jednym elementem: kolumna telefonu, znaleziono w bieżącej tabeli kolumn (listy 1), ale nie w powiązanych z zestawu rekordów kolumn (lista 2).  
  
3.  Tworzenie listy Dynamic-Values kolumny (jak lista 4 na ilustracji) do przechowywania wartości danych, odpowiadający nazwa kolumny przechowywane na liście kolumn, aby powiązać dynamicznie (kolumn do Bind — dynamiczne).  
  
     Elementy tej listy odtwarzania roli nowego zestawu rekordów elementy członkowskie danych pola. Są one lokalizacji przechowywania, do których dynamiczne kolumny są powiązane. Opisy list można znaleźć [listy kolumn](#_core_lists_of_columns).  
  
###  <a name="_core_providing_storage_for_the_new_columns"></a> Zapewnianie magazynowania dla nowych kolumn  
 Następnie skonfiguruj lokalizacje magazynu dla kolumn, które mają być dynamicznie powiązane. Chodzi o to, aby zapewnić elementu listy do przechowywania wartości w każdej kolumnie. Te lokalizacje magazynu równoległego zmienne Członkowskie zestawu rekordów, które przechowują zazwyczaj powiązane kolumny.  
  
##### <a name="to-provide-dynamic-storage-for-new-columns-dynamic-column-values"></a>Aby zapewnić pamięci dynamicznej dla nowych kolumn (kolumna-Dynamic-Values)  
  
1.  Twórz dynamiczne — — wartości kolumn, zbliżony do kolumn — do — powiązania-dynamicznie, zawiera wartość danych w każdej kolumnie.  
  
     Na przykład na ilustracji przedstawiono dynamiczne kolumny wartości (Lista 4) z jednym elementem: `CString` obiekt, który zawiera numer telefonu rzeczywiste dla bieżącego rekordu: "555-1212".  
  
     W przypadku najbardziej typowych wartości w przypadku kolumn dynamiczna ma elementów typu `CString`. Jeśli masz do czynienia z kolumnami różnych typów danych, konieczne będzie listę, która może zawierać elementy różnych typów.  
  
 Wynikiem powyższych procedur są dwie główne listy: kolumny do Bind — dynamicznie zawierająca nazwy kolumn i Dynamic-— wartości kolumny zawierające wartości w kolumnach dla bieżącego rekordu.  
  
> [!TIP]
>  Jeśli nowych kolumn nie są wszystkie tego samego typu danych, możesz zechcieć paraleli dodatkowych listy zawierającej elementy, które jakiś sposób definiowania typu każdy odpowiadający mu element na liście kolumn. (Można użyć wartości AFX_RFX_BOOL, AFX_RFX_BYTE, i tak dalej dla to, jeśli chcesz otrzymywać. Te stałe są definiowane w AFXDB. H.) Wybierz typ listy, w oparciu o sposób przedstawiania column — typy danych.  
  
###  <a name="_core_adding_rfx_calls_to_bind_the_columns"></a> Dodawanie połączeń RFX powiązać kolumny  
 Na koniec organizuje wiązanie dynamiczne wystąpią, umieszczając RFX wywołuje nowych kolumn w swojej `DoFieldExchange` funkcji.  
  
##### <a name="to-dynamically-add-rfx-calls-for-new-columns"></a>Dynamicznie dodać RFX wymaga nowych kolumn  
  
1.  W głównym zestawie rekordów `DoFieldExchange` element członkowski funkcji, Dodaj kod, który pętli listę nowych kolumn (kolumn do Bind — dynamiczne). W każdej pętli Wyodrębnij nazwę kolumny z kolumny — do — powiązania — dynamiczne i wartości wyniku dla kolumny z wartości w przypadku kolumn dynamiczny. Przekaż te elementy do wywołania funkcji RFX odpowiednie dla typu danych kolumny. Opisy list można znaleźć [listy kolumn](#_core_lists_of_columns).  
  
 W typowych przypadkach w swojej `RFX_Text` wyodrębniania wywołaniach funkcji `CString` obiekty z listy, tak jak w następujące wiersze kodu, gdzie jest kolumn do Bind — dynamicznie `CStringList` o nazwie `m_listName` i wartości w przypadku kolumn dynamiczny jest `CStringList` o nazwie `m_listValue`:  
  
```cpp  
RFX_Text( pFX,   
            m_listName.GetNext( posName ),   
            m_listValue.GetNext( posValue ));  
```  
  
 Aby uzyskać więcej informacji na temat funkcji RFX zobacz [makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md) w *odwołanie do biblioteki klas*.  
  
> [!TIP]
>  Jeśli nowe kolumny są różnych typów danych, należy użyć instrukcji switch w pętlę metodyki wywołanie odpowiedniej funkcji RFX dla każdego typu.  
  
 Kiedy struktura wywołuje `DoFieldExchange` podczas `Open` proces, aby powiązać kolumny zestawu rekordów, wywołania RFX dla statycznych kolumn powiązać te kolumny. Następnie pętlę metodyki wielokrotnie wywołuje funkcje RFX dynamiczne kolumn.  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Zestaw rekordów: praca z dużymi elementami danych (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)