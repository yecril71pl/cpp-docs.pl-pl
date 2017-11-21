---
title: "Zestaw rekordów: Jak AddNew, Edit i Delete działają (ODBC) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- records [C++], updating
- record editing [C++], in recordsets
- recordsets [C++], adding records
- records [C++], adding
- ODBC recordsets [C++], adding records
- recordsets [C++], editing records
- recordsets [C++], updating
- AddNew method
- ODBC recordsets [C++], deleting records
- records [C++], deleting in recordsets
- data in recordsets [C++]
- recordsets [C++], deleting records
- ODBC recordsets [C++], editing records
- records [C++], editing
ms.assetid: cab43d43-235a-4bed-ac05-67d10e94f34e
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bc26033ff0da5c49ddcb848f648925978f7b53da
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="recordset-how-addnew-edit-and-delete-work-odbc"></a>Zestaw rekordów: jak działają funkcje AddNew, Edit i Delete (ODBC)
Ten temat dotyczy klasach MFC ODBC.  
  
 W tym temacie opisano sposób `AddNew`, **Edytuj**, i **usunąć** funkcji elementów członkowskich klasy `CRecordset` pracy. Tematy obejmują:  
  
-   [Jak dodać rekordy działania](#_core_adding_a_record)  
  
-   [Widoczność dodanych rekordów](#_core_visibility_of_added_records)  
  
-   [Jak działa edytowanie rekordów](#_core_editing_an_existing_record)  
  
-   [Sposób usuwania działania rekordów](#_core_deleting_a_record)  
  
> [!NOTE]
>  Ten temat dotyczy obiektów pochodzących od `CRecordset` w wiersz, który zbiorczego pobierania nie została zaimplementowana. Jeśli korzystasz z zbiorcze pobieranie z wiersza, zobacz [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Jako uzupełnienie, należy przeczytać [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md), która opisuje odpowiedniej roli RFX w operacjach aktualizowania.  
  
##  <a name="_core_adding_a_record"></a>Dodawanie rekordów  

 Dodawanie nowego rekordu do zestawu rekordów obejmuje wywoływanie w zestawie rekordów [AddNew](../../mfc/reference/crecordset-class.md#addnew) funkcji członkowskiej, ustawienie wartości elementy członkowskie danych pola w nowym rekordzie i wywoływania [aktualizacji](../../mfc/reference/crecordset-class.md#update) funkcji członkowskiej do zapisania rekord w źródle danych.  
  
 Jako warunek wstępny dotyczący wywołania `AddNew`, zestaw rekordów musi nie został otwarty jako tylko do odczytu. `CanUpdate` i `CanAppend` funkcji członkowskich pozwalają określić te warunki.  
  
 Podczas wywoływania `AddNew`:  
  
-   Rekord w buforze edycji są przechowywane, mogą zostać przywrócone jego zawartość, jeśli operacja została anulowana.  
  
-   Elementy członkowskie danych pola są oznaczane, dzięki czemu można wykryć zmiany w ich później. Elementy członkowskie są również oznaczane danych pola czyszczenia (bez zmian) i ustawić na wartość Null.  
  
 Po wywołaniu metody `AddNew`buforu edycji reprezentuje nowy, pusty rekord, gotowe w celu wprowadzenia wartości. Aby to zrobić, należy ręcznie ustawić wartości przez przypisanie do nich. Zamiast określania wartości rzeczywistych danych pola, można wywołać `SetFieldNull` można określić wartości Null.  
  
 Aby zatwierdzić zmiany, należy wywołać **aktualizacji**. Podczas wywoływania **aktualizacji** w nowym rekordzie:  
  
-   Jeśli sterownik ODBC obsługuje **:: SQLSetPos** funkcji interfejsu API ODBC MFC za pomocą funkcji Dodaj rekord w źródle danych. Z **:: SQLSetPos**, MFC można dodać rekordu wydajniej, ponieważ nie ma do tworzenia i przetwarzania instrukcji SQL.  
  
-   Jeśli **:: SQLSetPos** nie może być używany, MFC wykonuje następujące czynności:  
  
    1.  Jeśli nie wykryto żadnych zmian, **aktualizacji** nie robi nic i zwraca wartość 0.  
  
    2.  Jeśli istnieją zmiany, **aktualizacji** tworzy SQL **Wstaw** instrukcji. Kolumn reprezentowanych przez wszystkie elementy członkowskie danych pola z zanieczyszczeniu są wymienione w **Wstaw** instrukcji. Aby wymusić kolumny, które zostaną uwzględnione, należy wywołać [SetFieldDirty](../../mfc/reference/crecordset-class.md#setfielddirty) funkcji członkowskiej:  
  
        ```  
        SetFieldDirty( &m_dataMember, TRUE );  
        ```  
  
    3.  **Aktualizacja** zatwierdza nowy rekord — **Wstaw** instrukcja jest wykonywana i rekord zostanie przekazany do tabeli w źródle danych (i zestaw rekordów, jeśli nie migawkę), chyba że transakcja jest w toku.  
  
    4.  Po przywróceniu rekordu przechowywanych w buforze edycji. Rekord, które były aktualne przed `AddNew` wywołanie jest ponownie niezależnie od tego, czy bieżący **Wstaw** została pomyślnie wykonana.  
  
    > [!TIP]
    >  Dla pełną kontrolę nad nowego rekordu, należy wykonać następujące podejście: Ustaw wartości wszystkich pól, które będzie mieć wartości, a następnie jawnie ustaw wszystkie pola, które pozostanie Null przez wywołanie metody `SetFieldNull` za pomocą wskaźnika do pola i parametr **TRUE**  (ustawienie domyślne). Jeśli chcesz upewnić się, czy pole nie jest zapisywany w źródle danych, wywołanie `SetFieldDirty` za pomocą wskaźnika do pola i parametr **FALSE**i nie należy modyfikować wartości pola. Aby ustalić, czy pole może mieć wartości Null, należy wywołać `IsFieldNullable`.  
  
    > [!TIP]
    >  Do wykrycia, gdy elementy członkowskie danych zestawu rekordów, zmień wartość używa MFC **PSEUDO_NULL** wartość odpowiednią dla każdego typu danych, które można przechowywać w zestawie rekordów. Jeśli pole musi jawnie ustawiona na **PSEUDO_NULL** pola i wartość już stanie się być oznaczone Null, należy także wywołać `SetFieldNull`, przekazywanie adresu pola w pierwszym parametrze i **FALSE**w drugi parametr.  
  
##  <a name="_core_visibility_of_added_records"></a>Widoczność dodanych rekordów  
 Gdy dodano rekord jest widoczny dla zestawu rekordów Dodano rekordów czasami pojawiają się i czasami nie są widoczne w zależności od dwie czynności:  
  
-   Jakie sterownik jest w stanie.  
  
-   Jaką platformę można korzystać z.  
  
 Jeśli sterownik ODBC obsługuje **:: SQLSetPos** funkcji interfejsu API ODBC MFC używa funkcji, aby dodać rekordy. Z **:: SQLSetPos**, dodać rekordy są widoczne dla żadnych nadaje się do aktualizacji zestawu rekordów MFC. Bez obsługi funkcji, należy dodać rekordy nie są widoczne i należy wywołać **Requery** je wyświetlić. Przy użyciu **:: SQLSetPos** jest również bardziej efektywne.  
  
##  <a name="_core_editing_an_existing_record"></a>Edytowanie istniejącego rekordu  
 Edytowanie istniejącego rekordu w zestawie rekordów obejmuje przewijanie do rekordu wywoływanie w zestawie rekordów [Edytuj](../../mfc/reference/crecordset-class.md#edit) funkcji członkowskiej, ustawienie wartości elementy członkowskie danych pola w nowym rekordzie i wywoływania [aktualizacji](../../mfc/reference/crecordset-class.md#update)funkcji członkowskiej można zapisać zmienionych rekordów w źródle danych.  
  
 Jako warunek wstępny dotyczący wywołania **Edytuj**, zestaw rekordów musi być nadaje się do aktualizacji i w rekordzie. `CanUpdate` i `IsDeleted` funkcji członkowskich pozwalają określić te warunki. Bieżącego rekordu również musi nie już zostać usunięte, a musi być rekordy w zestawie rekordów (zarówno `IsBOF` i `IsEOF` zwraca 0).  
  
 Podczas wywoływania **Edytuj**, znajduje rekord w buforze edycji (bieżącego). Rekord przechowywanej wartości później są używane do wykrywania, czy wszystkie pola zostały zmienione.  
  
 Po wywołaniu metody **Edytuj**, buforu edycji nadal reprezentuje bieżącego rekordu, ale jest teraz gotowy do przyjęcia zmian elementy członkowskie danych pola. Aby zmienić rekordu, możesz ręcznie ustawić wartości wszystkie elementy członkowskie danych pola, które chcesz edytować. Zamiast określania wartości rzeczywistych danych pola, można wywołać `SetFieldNull` można określić wartości Null. Aby zatwierdzić zmiany, należy wywołać **aktualizacji**.  
  
> [!TIP]
>  Można pobrać z `AddNew` lub **Edytuj** tryb, wywołanie **Przenieś** z parametrem **AFX_MOVE_REFRESH**.  
  
 Jako warunek wstępny dotyczący wywołania **aktualizacji**, zestaw rekordów nie może być pusta i bieżącego rekordu nie musiały zostać usunięte. `IsBOF`, `IsEOF`, i `IsDeleted` powinien zwrócić 0.  
  
 Podczas wywoływania **aktualizacji** edytowanego rekordu:  
  
-   Jeśli sterownik ODBC obsługuje **:: SQLSetPos** funkcji interfejsu API ODBC MFC funkcja do zaktualizowania rekordu w źródle danych. Z **:: SQLSetPos**, sterownik porównuje z buforu edycji z odpowiedniego rekordu na serwerze, aktualizacja rekordu na serwerze, jeśli dwa są różne. Z **:: SQLSetPos**, MFC można zaktualizować rekord wydajniej, ponieważ nie ma do tworzenia i przetwarzania instrukcji SQL.  
  
     —lub—  
  
-   Jeśli **:: SQLSetPos** nie może być używany, MFC wykonuje następujące czynności:  
  
    1.  Jeżeli nie dokonano żadnych zmian, **aktualizacji** nie robi nic i zwraca wartość 0.  
  
    2.  Jeśli istnieją zmiany, **aktualizacji** tworzy SQL **aktualizacji** instrukcji. Kolumn na liście **aktualizacji** instrukcji są oparte na elementy członkowskie danych pola, które zostały zmienione.  
  
    3.  **Aktualizacja** zatwierdza zmiany — wykonuje **aktualizacji** instrukcji — i rekord zostało zmienione w źródle danych, ale jeśli nie zatwierdzić transakcji jest w toku (zobacz [transakcja: wykonywanie transakcji w zestaw rekordów (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md) informacji o wpływ aktualizacja transakcji). ODBC przechowuje kopie rekordu, co spowoduje również zmianę.  
  
    4.  W przeciwieństwie do procesu `AddNew`, **Edytuj** proces nie powoduje przywrócenia przechowywanych rekordu. Edytowany rekord jest uwzględniany jako bieżącego rekordu.  
  
    > [!CAUTION]
    >  Podczas przygotowania do aktualizacji zestawu rekordów przez wywołanie metody **aktualizacji**, zwrócić uwagę, że zestawu rekordów zawiera wszystkie kolumny tworzące klucz podstawowy tabeli (lub wszystkie kolumny dowolny unikatowy indeks w tabeli lub wystarczającej liczby kolumn do jednoznacznie Określ wiersz). W niektórych przypadkach framework może być zidentyfikować rekordy w tabeli, aby zaktualizować tylko kolumny wybrana w twoim zestawie rekordów. Nie wszystkie kolumny niezbędne wiele rekordów mogły zostać zaktualizowane w tabeli. W takim przypadku platformę zgłasza wyjątki podczas wywoływania **aktualizacji**.  
  
    > [!TIP]
    >  Jeśli wywołujesz `AddNew` lub **Edytuj** po wywołaniu funkcji albo wcześniej, ale zanim zajdzie wywołania **aktualizacji**, buforu edycji jest odświeżany z rekordem przechowywane, zastępując rekordu nowe lub zmodyfikowane w postęp. To zachowanie umożliwia przerwania `AddNew` lub **Edytuj** i rozpocząć nową: Jeśli okaże się, że rekord postępu jest uszkodzony, po prostu Wywołaj **Edytuj** lub `AddNew` ponownie.  
  
##  <a name="_core_deleting_a_record"></a>Usunięcie rekordu  
 Usunięcie rekordu z zestawu rekordów obejmuje przewijanie do rekordu i wywoływanie w zestawie rekordów [usunąć](../../mfc/reference/crecordset-class.md#delete) funkcję elementu członkowskiego. W odróżnieniu od `AddNew` i **Edytuj**, **usunąć** nie wymaga miejsce odpowiadające wywołanie **aktualizacji**.  
  
 Jako warunek wstępny dotyczący wywołania **usunąć**, zestaw rekordów musi zezwalać na aktualizacje, i musi znajdować się na rekordu. `CanUpdate`, `IsBOF`, `IsEOF`, I `IsDeleted` funkcji członkowskich pozwalają określić te warunki.  
  
 Podczas wywoływania **usunąć**:  
  
-   Jeśli sterownik ODBC obsługuje **:: SQLSetPos** funkcji interfejsu API ODBC MFC funkcja usuwanie rekordu w źródle danych. Przy użyciu **:: SQLSetPos** jest zazwyczaj bardziej efektywne niż przy użyciu programu SQL.  
  
     —lub—  
  
-   Jeśli **:: SQLSetPos** nie może być używany, MFC wykonuje następujące czynności:  
  
    1.  Rekord bieżący w buforze Edycja nie jest kopii zapasowej jako w `AddNew` i **Edytuj**.  
  
    2.  **Usuń** tworzy SQL **usunąć** instrukcji, która spowoduje usunięcie rekordu.  
  
         Rekord bieżący w buforze Edycja nie jest przechowywana jako w `AddNew` i **Edytuj**.  
  
    3.  **Usuń** zatwierdza usunięcia — wykonuje **usunąć** instrukcji. Rekord jest oznaczony jako usunięte w źródle danych i, jeśli rekord jest migawka w ODBC.  
  
    4.  Usuniętego rekordu wartości są nadal w elementy członkowskie danych pola zestawu rekordów, ale elementy członkowskie danych pola są oznaczone Null i w zestawie rekordów `IsDeleted` — członek, funkcja zwraca wartość różną od zera.  
  
    > [!NOTE]
    >  Po usunięciu rekordu, powinien przewiń do innego rekordu uzupełnienie edycji bufor nowego rekordu danych. Błąd do wywołania **usunąć** ponownie lub wywołać **Edytuj**.  
  
 Uzyskać informacje na temat instrukcji SQL, używane podczas wykonywania operacji aktualizacji, zobacz [SQL](../../data/odbc/sql.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Zestaw rekordów: Więcej informacji o aktualizacjach (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)   
 [Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md)