---
title: 'Zestaw rekordów: jak działają funkcje AddNew, Edit i Delete (ODBC)'
ms.date: 11/04/2016
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
ms.openlocfilehash: 8799ac36c443898f1e32b539f017e682bbf3e033
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212913"
---
# <a name="recordset-how-addnew-edit-and-delete-work-odbc"></a>Zestaw rekordów: jak działają funkcje AddNew, Edit i Delete (ODBC)

Ten temat dotyczy klas MFC ODBC.

W tym temacie wyjaśniono, jak `AddNew`, `Edit`i `Delete` funkcje członkowskie klasy `CRecordset` działają. Omawiane tematy to m.in.:

- [Jak działa Dodawanie rekordów](#_core_adding_a_record)

- [Widoczność dodanych rekordów](#_core_visibility_of_added_records)

- [Jak działa Edycja rekordów](#_core_editing_an_existing_record)

- [Jak działają usuwanie rekordów](#_core_deleting_a_record)

> [!NOTE]
>  Ten temat dotyczy obiektów pochodnych `CRecordset`, w których nie zaimplementowano pobierania wierszy zbiorczych. Jeśli używasz pobierania wierszy zbiorczych, zobacz [zestaw rekordów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Jako uzupełnienie możesz chcieć odczytać [wymianę pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md), która opisuje odpowiednią rolę RFX w operacjach aktualizacji.

##  <a name="adding-a-record"></a><a name="_core_adding_a_record"></a>Dodawanie rekordu

Dodawanie nowego rekordu do zestawu rekordów polega na wywołaniu funkcji elementu członkowskiego zestawu rekordów, ustawieniu wartości [elementów członkowskich danych](../../mfc/reference/crecordset-class.md#addnew) pola nowego rekordu i wywołaniu funkcji elementu członkowskiego [aktualizacji](../../mfc/reference/crecordset-class.md#update) w celu zapisania rekordu w źródle danych.

Jako warunek wstępny do wywoływania `AddNew`zestaw rekordów nie może być otwarty jako tylko do odczytu. `CanUpdate` i `CanAppend` funkcje członkowskie pozwalają określić te warunki.

Podczas wywoływania `AddNew`:

- Rekord w buforze edycji jest przechowywany, więc jego zawartość może zostać przywrócona, jeśli operacja została anulowana.

- Elementy członkowskie danych pola są oflagowane, więc możliwe jest ich późniejsze wykrycie. Elementy członkowskie danych pola są również oznaczone jako czyste (bez zmian) i mają ustawioną wartość null.

Po wywołaniu `AddNew`bufor edycji reprezentuje nowy, pusty rekord, gotowy do wypełnienia wartościami. W tym celu należy ręcznie ustawić wartości, przypisując je do nich. Zamiast określać rzeczywistą wartość danych dla pola, można wywołać `SetFieldNull`, aby określić wartość null.

Aby zatwierdzić zmiany, należy wywołać `Update`. Gdy wywołasz `Update` dla nowego rekordu:

- Jeśli sterownik ODBC obsługuje funkcję `::SQLSetPos` ODBC API, MFC używa funkcji, aby dodać rekord w źródle danych. Dzięki `::SQLSetPos`MFC może bardziej efektywnie dodawać rekordy, ponieważ nie ma potrzeby konstruowania i przetwarzania instrukcji SQL.

- Jeśli nie można użyć `::SQLSetPos`, MFC wykonuje następujące czynności:

   1. Jeśli nie wykryto żadnych zmian, `Update` nic nie robi i zwróci wartość 0.

   1. Jeśli istnieją zmiany, `Update` konstruuje instrukcję **INSERT** języka SQL. Kolumny reprezentowane przez wszystkie elementy członkowskie danych pól zanieczyszczonych są wymienione w instrukcji **INSERT** . Aby wymusić dołączenie kolumny, wywołaj funkcję członkowską [SetFieldDirty](../../mfc/reference/crecordset-class.md#setfielddirty) :

        ```cpp
        SetFieldDirty( &m_dataMember, TRUE );
        ```

   1. `Update` zatwierdza nowy rekord — instrukcja **INSERT** jest wykonywana, a rekord jest zatwierdzany do tabeli w źródle danych (a zestaw rekordów, jeśli nie jest migawką), chyba że transakcja jest w toku.

   1. Zapisany rekord zostanie przywrócony do buforu edycji. Rekord, który był aktualny przed wywołaniem `AddNew` jest ponownie bieżący, niezależnie od tego, czy instrukcja **INSERT** została wykonana pomyślnie.

   > [!TIP]
   > Aby uzyskać pełną kontrolę nad nowym rekordem, należy zastosować następujące podejście: Ustaw wartości pól, które będą mieć wartości, a następnie jawnie ustaw wszelkie pola, które pozostaną puste, wywołując `SetFieldNull` ze wskaźnikiem do pola i parametrem TRUE (wartość domyślna). Jeśli chcesz mieć pewność, że pole nie jest zapisywana w źródle danych, wywołaj `SetFieldDirty` ze wskaźnikiem do pola i parametrem FALSE i nie Modyfikuj wartości pola. Aby określić, czy pole może mieć wartość null, wywołaj `IsFieldNullable`.

   > [!TIP]
   > Aby wykryć, kiedy elementy członkowskie danych zestawu rekordów zmieniają wartość, MFC używa wartości PSEUDO_NULL odpowiedniej dla każdego typu danych, który można przechowywać w zestawie rekordów. Jeśli musisz jawnie ustawić pole na wartość PSEUDO_NULL i pole ma już oznaczenie null, należy również wywołać `SetFieldNull`, przekazując adres pola w pierwszym parametrze i wartość FALSE w drugim parametrze.

##  <a name="visibility-of-added-records"></a><a name="_core_visibility_of_added_records"></a>Widoczność dodanych rekordów

Kiedy dodano rekord widoczny dla zestawu rekordów? Dodane rekordy czasami są wyświetlane i czasami nie są widoczne, w zależności od dwóch elementów:

- Do czego służy Twój sterownik.

- Zalety platformy.

Jeśli sterownik ODBC obsługuje funkcję `::SQLSetPos` ODBC API, MFC używa funkcji, aby dodać rekordy. W `::SQLSetPos`dodane rekordy są widoczne dla dowolnego aktualizowalnego zestawu rekordów MFC. Bez obsługi funkcji, dodane rekordy nie są widoczne i należy wywołać `Requery`, aby je zobaczyć. Używanie `::SQLSetPos` jest również wydajniejsze.

##  <a name="editing-an-existing-record"></a><a name="_core_editing_an_existing_record"></a>Edytowanie istniejącego rekordu

Edytowanie istniejącego rekordu w zestawie rekordów obejmuje przewijanie do rekordu, wywoływanie funkcji [Edytuj](../../mfc/reference/crecordset-class.md#edit) element członkowski zestawu rekordów, ustawienie wartości elementów członkowskich danych pola nowego rekordu i wywołanie funkcji [aktualizacji](../../mfc/reference/crecordset-class.md#update) elementu członkowskiego, aby zapisać zmieniony rekord w źródle danych.

Jako warunek wstępny do wywoływania `Edit`, zestaw rekordów musi być aktualizowalny i w rekordzie. `CanUpdate` i `IsDeleted` funkcje członkowskie pozwalają określić te warunki. Bieżący rekord również nie może zostać usunięty i w zestawie rekordów muszą istnieć rekordy (zarówno `IsBOF`, jak i `IsEOF` zwracają 0).

Gdy wywołasz `Edit`, rekord w buforze edycji (bieżący rekord) jest przechowywany. Wartości przechowywanych rekordów są później używane do wykrywania, czy wszystkie pola zostały zmienione.

Po wywołaniu `Edit`bufor edycji nadal reprezentuje bieżący rekord, ale jest teraz gotowy do zaakceptowania zmian w elementach członkowskich danych pola. Aby zmienić rekord, ręcznie ustaw wartości wszelkich elementów członkowskich danych pól, które chcesz edytować. Zamiast określać rzeczywistą wartość danych dla pola, można wywołać `SetFieldNull`, aby określić wartość null. Aby zatwierdzić zmiany, wywołaj `Update`.

> [!TIP]
> Aby przejść do trybu `AddNew` lub `Edit`, wywołaj `Move` z *AFX_MOVE_REFRESH*parametru.

Jako warunek wstępny do wywoływania `Update`, zestaw rekordów nie może być pusty, a bieżący rekord nie może zostać usunięty. `IsBOF`, `IsEOF`i `IsDeleted` powinny zwrócić wartość 0.

Podczas wywoływania `Update` dla edytowanego rekordu:

- Jeśli sterownik ODBC obsługuje funkcję `::SQLSetPos` ODBC API, MFC używa funkcji, aby zaktualizować rekord w źródle danych. Przy `::SQLSetPos`Sterownik porównuje bufor edycji z odpowiednim rekordem na serwerze i aktualizuje rekord na serwerze, jeśli są różne. Dzięki `::SQLSetPos`MFC może wydajniej aktualizować rekord, ponieważ nie musi on tworzyć i przetwarzać instrukcji SQL.

   \- lub-

- Jeśli nie można użyć `::SQLSetPos`, MFC wykonuje następujące czynności:

   1. Jeśli nie wprowadzono żadnych zmian, `Update` nic nie robi i zwróci wartość 0.

   1. Jeśli istnieją zmiany, `Update` konstruuje instrukcję SQL **Update** . Kolumny wymienione w instrukcji **Update** są oparte na elementach członkowskich danych pól, które uległy zmianie.

   1. `Update` zatwierdza zmiany — wykonuje instrukcję **Update** , a rekord zostanie zmieniony w źródle danych, ale nie zostanie zatwierdzony, jeśli transakcja jest w toku (patrz [transakcja: wykonywanie transakcji w zestawie rekordów (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md) , aby uzyskać informacje o tym, jak transakcja wpływa na aktualizację). ODBC zachowuje kopię rekordu, która również ulega zmianie.

   1. W przeciwieństwie do procesu `AddNew`, proces `Edit` nie przywraca przechowywanego rekordu. Edytowany rekord pozostaje w miejscu w bieżącym rekordzie.

   > [!CAUTION]
   > Podczas przygotowywania do aktualizowania zestawu rekordów przez wywoływanie `Update`należy zadbać o to, aby zestaw rekordów zawierał wszystkie kolumny tworzące klucz podstawowy tabeli (lub wszystkie kolumny dowolnego unikatowego indeksu w tabeli, lub wystarczającą liczbę kolumn, aby jednoznacznie identyfikować wiersz). W niektórych przypadkach struktura może używać tylko kolumn wybranych w zestawie rekordów, aby identyfikować, który rekord w tabeli należy zaktualizować. Bez wszystkich wymaganych kolumn w tabeli można zaktualizować wiele rekordów. W takim przypadku platforma zgłasza wyjątki podczas wywoływania `Update`.

   > [!TIP]
   > Jeśli wywołasz `AddNew` lub `Edit` po wywołaniu funkcji wcześniej, ale przed wywołaniem `Update`, bufor edycji zostanie odświeżony z przechowywanym rekordem, zastępując nowy lub edytowany rekord w toku. To zachowanie umożliwia przerwanie `AddNew` lub `Edit` i rozpoczęcie nowego: Jeśli ustalisz, że rekord w toku jest uszkodzony, po prostu wywołaj `Edit` lub `AddNew` ponownie.

##  <a name="deleting-a-record"></a><a name="_core_deleting_a_record"></a>Usuwanie rekordu

Usunięcie rekordu z zestawu rekordów obejmuje przewinięcie do rekordu i wywołanie funkcji [usuwania](../../mfc/reference/crecordset-class.md#delete) elementu członkowskiego zestawu rekordów. W przeciwieństwie do `AddNew` i `Edit``Delete` nie wymaga zgodnego wywołania do `Update`.

Jako warunek wstępny do wywoływania `Delete`, zestaw rekordów musi być aktualizowalny i musi znajdować się na rekordzie. `CanUpdate`, `IsBOF`, `IsEOF`i `IsDeleted` funkcje członkowskie pozwalają określić te warunki.

Podczas wywoływania `Delete`:

- Jeśli sterownik ODBC obsługuje funkcję `::SQLSetPos` ODBC API, MFC używa funkcji, aby usunąć rekord ze źródła danych. Używanie `::SQLSetPos` jest zwykle bardziej wydajne niż używanie języka SQL.

   \- lub-

- Jeśli nie można użyć `::SQLSetPos`, MFC wykonuje następujące czynności:

   1. Nie utworzono kopii zapasowej bieżącego rekordu w buforze edycji, jak w `AddNew` i `Edit`.

   1. `Delete` konstruuje instrukcję **delete** języka SQL, która usuwa rekord.

      Bieżący rekord w buforze edycji nie jest przechowywany w `AddNew` i `Edit`.

   1. `Delete` zatwierdza usuwanie — wykonuje instrukcję **delete** . Rekord jest oznaczony jako usunięty w źródle danych i, jeśli rekord jest migawką, w ODBC.

   1. Wartości usuniętych rekordów nadal znajdują się w elementach członkowskich danych pola, ale elementy członkowskie danych pola są oznaczone jako null, a funkcja członkowska `IsDeleted` zestawu rekordów zwraca wartość różną od zera.

   > [!NOTE]
   > Po usunięciu rekordu należy przewinąć do innego rekordu w celu ponownego wypełnienia buforu edycji z danymi nowego rekordu. Wystąpił błąd, aby ponownie wywołać `Delete` lub wywołać `Edit`.

Aby uzyskać informacje na temat instrukcji SQL używanych w operacjach aktualizacji, zobacz [SQL](../../data/odbc/sql.md).

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: więcej informacji o aktualizacjach (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)<br/>
[Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md)
