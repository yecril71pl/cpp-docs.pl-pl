---
title: 'Zestaw rekordów: Dynamiczne wiązanie kolumn danych (ODBC) | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 9fe71707de20ba02228039e5693cab9c9401d560
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="recordset-dynamically-binding-data-columns-odbc"></a>Zestaw rekordów: dynamiczne powiązanie kolumn danych (ODBC)
Ten temat dotyczy klasach MFC ODBC.  
  
 Zestawy rekordów zarządzać powiązanie kolumn tabeli, które określisz w czasie projektowania, ale istnieją przypadki, jeśli chcesz powiązać kolumny, które były nieznane do użytkownika w czasie projektowania. W tym temacie opisano:  
  
-   [Kiedy warto dynamicznie powiązać kolumny zestawu rekordów](#_core_when_you_might_bind_columns_dynamically).  
  
-   [Jak można powiązać kolumny dynamicznie w czasie wykonywania](#_core_how_to_bind_columns_dynamically).  
  
> [!NOTE]
>  Ten temat dotyczy obiektów pochodzących od `CRecordset` w wiersz, który zbiorczego pobierania nie została zaimplementowana. Techniki opisane zazwyczaj nie są zalecane, jeśli używasz zbiorcze pobieranie z wiersza. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="_core_when_you_might_bind_columns_dynamically"></a> Gdy może powiązać kolumny dynamicznie  
 W czasie projektowania, Kreator aplikacji MFC lub [Kreator konsumenta MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) (z **Dodaj klasę**) tworzy klasy rekordów na podstawie znanych tabel i kolumn w źródle danych. Bazy danych można zmieniać, podczas projektowania ich i nowszym, jeśli aplikacja korzysta z tych tabel i kolumn w czasie wykonywania. Użytkownika może dodać lub Porzuć tabelę lub dodać lub porzucić kolumny z tabeli, która zależy od aplikacji zestawu rekordów. To prawdopodobnie nie ma znaczenia dla wszystkich aplikacji dostęp do danych, ale jeśli należy do Ciebie, jak możesz zgodnie z zmiany w schemacie bazy danych, innych niż przez zmodyfikowanie i ponownej kompilacji? W tym temacie ma na celu odpowiedzi na to pytanie.  
  
 W tym temacie opisano najbardziej typowych przypadkach, w którym może powiązać kolumny dynamicznie — o uruchomione za pomocą zestawu rekordów na podstawie schematu znane bazy danych, chcesz obsługiwać dodatkowe kolumny w czasie wykonywania. Temat dalszych zakłada mapowania dla dodatkowych kolumn `CString` pola elementy członkowskie danych, najbardziej typowych przypadkach, mimo że sugestie są dostarczane w celu zarządzania innymi typami danych.  
  
 Mała ilość dodatkowego kodu można:  
  
-   [Określić, które kolumny są dostępne w czasie wykonywania](#_core_how_to_bind_columns_dynamically).  
  
-   [Powiązać dodatkowe kolumny zestawu rekordów dynamicznie w czasie wykonywania](#_core_adding_the_columns).  
  
 Zestawu rekordów nadal zawiera elementy członkowskie danych dla kolumny, które wiedzieli o w czasie projektowania. Także zawiera niewielki dodatkowy kod, który dynamicznie Określa, czy wszystkie nowe kolumny zostały dodane do tabeli docelowej i, jeśli tak, wiąże te nowe kolumny do magazynu dynamicznie przydzielonego (a nie do elementów członkowskich zestawu rekordów danych).  
  
 Ten temat nie obejmuje innych przypadkach wiązania dynamicznego, takich jak porzuconych tabel lub kolumn. Dla tych przypadków musisz użyć wywołania interfejsu API ODBC bardziej bezpośrednio. Aby uzyskać informacje, zobacz ODBC SDK *Podręcznik programisty* na dysku CD biblioteki MSDN.  
  
##  <a name="_core_how_to_bind_columns_dynamically"></a> Jak dynamicznie powiązanie kolumn  
 Dynamiczne powiązanie kolumn, musisz znać (lub być możliwe ustalenie) nazwy dodatkowych kolumn. Musi również przydzielić magazyn elementów członkowskich danych dodatkowego pola, określ ich nazwy i typy i określ liczbę kolumn, które dodajesz.  
  
 Następujące dyskusji wymienia dwóch różnych zestawów rekordów. Pierwsza to główny zestaw rekordów, które wybiera rekordy z tabeli docelowej. Drugim jest używany do uzyskiwania informacji na temat kolumn w tabeli docelowej specjalnej kolumny zestawu rekordów.  
  
###  <a name="_core_the_general_process"></a> Proces ogólne  
 Najbardziej ogólnego poziomu, wykonaj następujące kroki:  
  
1.  Utworzyć obiekt główny zestaw rekordów.  
  
     Opcjonalnie można przekazać wskaźnik do otwartego `CDatabase` obiektu lub podać informacje o połączeniu kolumny zestawu rekordów w inny sposób.  
  
2.  Czynności można dodać kolumny dynamicznie.  
  
     Zapoznaj się z procesem opisanym w Dodawanie kolumn poniżej.  
  
3.  Otwórz głównego zestawu rekordów.  
  
     Zestaw rekordów wybiera rekordów i używa wymiana pól rekordów (RFX) można powiązać zarówno statyczne (te mapowane na elementy członkowskie danych pola rekordów) i dynamiczna kolumn (przypisane do dodatkowego magazynu, jaką można przydzielić).  
  
###  <a name="_core_adding_the_columns"></a> Dodawanie kolumn  
 Dynamiczne wiązanie dodane kolumn w czasie wykonywania wymaga wykonania następujących czynności:  
  
1.  Określ w czasie wykonywania, co to są kolumny w tabeli docelowej. Wyodrębnij dane listy kolumn, które zostały dodane do tabeli, ponieważ klasy rekordów została zaprojektowana.  
  
     Dobre rozwiązanie jest używanie klasy kolumny zestawu rekordów zaprojektowane, aby zbadać źródło danych, aby uzyskać informacje dotyczące kolumn dla tabeli docelowej (takie jak typ danych kolumny).  
  
2.  Zapewnianie magazynowania dla nowe elementy członkowskie danych pola. Ponieważ klasy głównym rekordów nie ma nieznany kolumn, elementy członkowskie danych pola, musisz podać miejsce do przechowywania nazw, wyniki i prawdopodobnie typu danych (jeśli kolumn są różne typy danych).  
  
     Jednym z podejść jest utworzenie co najmniej jednego dynamicznego list, jeden dla nazwy nowe kolumny, innej wartości wyników i innych ich typów danych (w razie potrzeby). Te listy, szczególnie na liście wartości, podaj informacje i niezbędne magazynu dla powiązania. Na poniższym rysunku przedstawiono tworzenie listy.  
     ![Tworzenie listy kolumn, które można powiązać dynamicznie](../../data/odbc/media/vc37w61.gif "vc37w61")  
Tworzenie listy kolumn do powiązanego dynamicznie  
  
3.  Dodaj wywołanie funkcji RFX w głównym zestawu rekordów `DoFieldExchange` funkcji dla poszczególnych dodanych kolumn. Te wywołania RFX pracy Pobieranie rekordu, włączając dodatkowe kolumny i powiązanie kolumn do elementów członkowskich zestawu rekordów danych lub pamięć masową dynamicznie dostarczony dla nich.  
  
     Jednym z podejść jest dodanie pętlę do głównego zestawu rekordów `DoFieldExchange` funkcji, który przetwarza w pętli listy nowe kolumny wywołanie odpowiedniej funkcji RFX dla każdej kolumny na liście. Przy każdym wywołaniu RFX przekazać nazwę kolumny z listy nazwy kolumn i lokalizację przechowywania w odpowiedni element członkowski listy wartości wyników.  
  
###  <a name="_core_lists_of_columns"></a> Lista kolumn  
 Cztery listy potrzebnych do pracy z przedstawiono w poniższej tabeli.  
  
 **Bieżącej tabeli kolumn (listy 1 na ilustracji)** listy kolumn w tabeli w źródle danych. Ta lista może być zgodny z listą kolumn obecnie powiązana w twoim zestawie rekordów.  
  
 **Powiązane z zestawu rekordów kolumn (2 listy na ilustracji)**  
 Lista kolumn powiązana w twoim zestawie rekordów. Te kolumny już RFX instrukcje w Twojej `DoFieldExchange` funkcji.  
  
 **Kolumny-do-Bind-dynamicznie (3 listy na ilustracji)**  
 Lista kolumn w tabeli, ale nie w twoim zestawie rekordów. To są kolumny, które chcesz powiązać dynamicznie.  
  
 **Dynamiczne kolumny wartości (4 listy na ilustracji)**  
 Lista zawierająca magazynu dla wartości jest pobierana z kolumny, które można powiązać dynamicznie. Elementy na tej liście odpowiadają w kolumn do Bind-dynamicznie, jeden-do-jednego.  
  
###  <a name="_core_building_your_lists"></a> Tworzenie list  
 Ze strategią ogólne, pamiętając można włączyć do szczegółowych informacji. Procedury przedstawione w pozostałej części tego tematu opisano, jak tworzyć listy pokazano [listy kolumn](#_core_lists_of_columns). Procedury przeprowadzają użytkownika przez proces:  
  
-   [Określanie nazwy kolumn nie zestawu rekordów](#_core_determining_which_table_columns_are_not_in_your_recordset).  
  
-   [Zapewnienie pamięci dynamicznej dla nowo dodanych do tabeli kolumn](#_core_providing_storage_for_the_new_columns).  
  
-   [Dynamiczne dodawanie RFX odwołuje się do kolumny](#_core_adding_rfx_calls_to_bind_the_columns).  
  
###  <a name="_core_determining_which_table_columns_are_not_in_your_recordset"></a> Określanie kolumny tabeli są spoza zestawu rekordów  
 Tworzenie listy (granica-kolumny zestawu rekordów-, jak lista 2 na ilustracji) zawierający listę kolumn już powiązane w głównym zestawu rekordów. Następnie można utworzyć listy (kolumn do Bind-dynamicznie, pochodzących z bieżącej tabeli kolumn i kolumny w przypadku zestawu rekordów powiązanego), która zawiera nazwy kolumn, które są w tabeli w źródle danych, ale nie w głównym zestawu rekordów.  
  
##### <a name="to-determine-the-names-of-columns-not-in-the-recordset-columns-to-bind-dynamically"></a>Aby poznać nazwy kolumn nie znajduje się w zestawie rekordów (kolumny do Bind-dynamicznie)  
  
1.  Tworzenie listy (ruch kolumny powiązane z zestawu rekordów) kolumny już powiązane w głównym zestawu rekordów.  
  
     Jednym z podejść jest można utworzyć kolumny w przypadku zestawu rekordów powiązanego w czasie projektowania. Wywołania funkcji RFX w zestawie rekordów można wizualnego `DoFieldExchange` funkcji, aby pobrać te nazwy. Następnie należy skonfigurować listy jako tablica zainicjowana z nazwami.  
  
     Na przykład na ilustracji przedstawiono powiązane z zestawu rekordów kolumn (lista 2) z trzech elementów. Kolumny w przypadku zestawu rekordów powiązanego brakuje kolumny telefonu wyświetlany w bieżącej tabeli kolumn (listy 1).  
  
2.  Porównanie bieżącej tabeli kolumn i kolumny w przypadku zestawu rekordów powiązanego do tworzenia listy (kolumny do Bind-dynamicznie) kolumn nie jest już powiązana w głównym zestawu rekordów.  
  
     Jednym z podejść jest pętli listy kolumn w tabeli w czasie wykonywania (ruch kolumny bieżącej tabeli) i na liście kolumn już powiązany w twoim zestawie rekordów (ruch kolumny powiązane z zestawu rekordów) równolegle. W kolumn do Bind-dynamicznie umieścić żadnych nazw w bieżącym--kolumn tabeli, które nie są wyświetlane w kolumnach powiązanych — zestaw rekordów.  
  
     Na przykład na ilustracji przedstawiono kolumny do Bind-dynamicznie (listy 3) z jednym elementem: kolumna Phone znalezione w bieżącej tabeli kolumn (listy 1), ale nie w powiązanych z zestawu rekordów kolumn (lista 2).  
  
3.  Tworzenie listy dynamicznie kolumny wartości (jak lista 4 na ilustracji) do przechowywania wartości danych odpowiadające każdej nazwa kolumny przechowywane na liście kolumn, aby powiązać dynamicznie (kolumny do Bind-dynamicznie).  
  
     Elementy tej listy odtwarzania roli nowego zestawu rekordów elementy członkowskie danych pola. Są one lokalizacji przechowywania, do których są powiązane kolumny dynamicznych. Opisy list, zobacz [listy kolumn](#_core_lists_of_columns).  
  
###  <a name="_core_providing_storage_for_the_new_columns"></a> Zapewnienie magazynu dla nowej kolumny  
 Następnie należy skonfigurować lokalizacje magazynu dla kolumny, które mają być dynamicznie powiązane. Koncepcja jest zapewnienie element listy do przechowywania wartości każdej kolumny. Te lokalizacje przechowywania równoległe zmienne Członkowskie zestawu rekordów, które przechowują zwykle powiązane kolumny.  
  
##### <a name="to-provide-dynamic-storage-for-new-columns-dynamic-column-values"></a>Dynamiczne magazynowanie nowe kolumny (dynamiczny-kolumny wartości)  
  
1.  Tworzenie dynamiczne —-wartości w kolumnach, zbliżony do kolumn do Bind — dynamicznie, zawiera wartość danych w każdej kolumnie.  
  
     Na przykład na ilustracji przedstawiono dynamicznie kolumny wartości (listy 4) z jednym elementem: `CString` obiektu zawierającego numer telefonu rzeczywiste dla bieżącego rekordu: "555-1212".  
  
     W przypadku najbardziej typowych dynamicznie kolumny wartości ma elementy typu `CString`. Mamy do czynienia z kolumnami różnych typów danych, należy najpierw listę, która może zawierać elementy różnych typów.  
  
 Wynikiem powyższych procedurach jest dwie listy głównego: kolumn do Bind-dynamicznie zawierająca nazwy kolumn i dynamicznie-kolumny — wartości zawierającą wartości w kolumnach dla bieżącego rekordu.  
  
> [!TIP]
>  Nowe kolumny nie znajdują się tego samego typu danych, możesz dodatkowe równoległe listy zawierającej elementy, które jakiś sposób definiowania typu każdego odpowiadającego mu elementu na liście kolumn. (Można użyć wartości **AFX_RFX_BOOL**, **AFX_RFX_BYTE**i tak dalej na to, jeśli chcesz. Te stałe są definiowane w AFXDB. H) Wybierz typ listy oparte na jak reprezentują typy danych kolumn.  
  
###  <a name="_core_adding_rfx_calls_to_bind_the_columns"></a> Dodanie rozmowy RFX powiązać kolumny  
 Na koniec organizuje wiązania dynamicznego występuje przez umieszczenie RFX wymaga nowe kolumny w Twojej `DoFieldExchange` funkcji.  
  
##### <a name="to-dynamically-add-rfx-calls-for-new-columns"></a>Dynamiczne dodawanie RFX wymaga nowe kolumny.  
  
1.  W głównym zestawu rekordów `DoFieldExchange` elementu członkowskiego działać, Dodaj kod, który przetwarza w pętli listę nowych kolumn (kolumny do Bind-dynamicznie). W każdej pętli Wyodrębnij nazwę kolumny z kolumny do Bind-dynamicznie i wartość wyniku dla kolumny z dynamicznie kolumny wartości. Przekaż te elementy do wywołania funkcji RFX odpowiednim dla typu danych kolumny. Opisy list, zobacz [listy kolumn](#_core_lists_of_columns).  
  
 W typowych przypadkach w Twojej `RFX_Text` funkcji wywołania wyodrębniania `CString` obiektów z list, jak w następujących wierszach kodu, gdzie kolumny do Bind-dynamicznie jest `CStringList` o nazwie `m_listName` i dynamicznie kolumny wartości jest `CStringList` o nazwie `m_listValue`:  
  
```  
RFX_Text( pFX,   
            m_listName.GetNext( posName ),   
            m_listValue.GetNext( posValue ));  
```  
  
 Aby uzyskać więcej informacji na temat funkcji RFX, zobacz [makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md) w *informacje dotyczące biblioteki klas*.  
  
> [!TIP]
>  Jeśli nowe kolumny są różne typy danych, umożliwia instrukcji switch w Twojej pętli wywołanie funkcji RFX odpowiednie dla każdego typu.  
  
 Gdy struktura wywołuje `DoFieldExchange` podczas **Otwórz** procesu, aby powiązać kolumny zestawu rekordów, wywołania RFX dla statycznych kolumn powiązać te kolumny. Następnie z pętli wielokrotnie wywołuje funkcje RFX dynamiczne kolumn.  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Zestaw rekordów: praca z dużymi elementami danych (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)