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
ms.openlocfilehash: 84d4c2f1128f7b73189f69b056eee96619c31ef5
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51331974"
---
# <a name="recordset-how-addnew-edit-and-delete-work-odbc"></a>Zestaw rekordów: jak działają funkcje AddNew, Edit i Delete (ODBC)

Ten temat dotyczy klas MFC ODBC.

W tym temacie opisano sposób, w jaki `AddNew`, `Edit`, i `Delete` funkcji elementów członkowskich klasy `CRecordset` pracy. Omawiane tematy to m.in.:

- [Jak działa rekordy dodawania](#_core_adding_a_record)

- [Widoczność dodano rekordów](#_core_visibility_of_added_records)

- [Jak działa edytowanie rekordów](#_core_editing_an_existing_record)

- [Jak usunąć działa rekordów](#_core_deleting_a_record)

> [!NOTE]
>  Ten temat dotyczy obiektów pochodzących od `CRecordset` w wierszu zbiorczego, które podczas pobierania nie została zaimplementowana. Jeśli używasz zbiorcze pobieranie z wiersza, zobacz [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Jako uzupełnienie, warto przeczytać [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md), która opisuje odpowiedniej roli RFX podczas operacji aktualizacji.

##  <a name="_core_adding_a_record"></a> Dodawanie rekordu

Dodawanie nowego rekordu do zestawu rekordów polega na wywołaniu zestawu rekordów [działają funkcje AddNew](../../mfc/reference/crecordset-class.md#addnew) funkcji członkowskiej, ustawianie wartości elementów członkowskich danych pola nowego rekordu i wywoływania [aktualizacji](../../mfc/reference/crecordset-class.md#update) funkcja elementu członkowskiego, aby zapisać rekord do źródła danych.

Jako warunek wstępny do wywoływania `AddNew`, zestaw rekordów musi nie został otwarty jako tylko do odczytu. `CanUpdate` i `CanAppend` funkcje Członkowskie pozwalają na określenie tych warunków.

Gdy wywołujesz `AddNew`:

- Rekord w buforze edycji są przechowywane, dzięki czemu można go przywrócić jego zawartość, jeśli operacja została anulowana.

- Elementy członkowskie danych pola są oznaczone, dzięki czemu umożliwia wykrywanie zmian w ich później. Pola danych elementów członkowskich są również oznaczane wyczyścić (bez zmian) i ustaw na wartość Null.

Po wywołaniu metody `AddNew`buforu edycji reprezentuje nowy, pusty rekord, gotowe w celu wprowadzenia wartości. Aby to zrobić, możesz ręcznie ustawić wartości przez przypisywanie do nich. Zamiast określania rzeczywista wartość danych dla pola, można wywołać `SetFieldNull` określić wartość Null.

Aby zatwierdzić zmiany, należy wywołać `Update`. Gdy wywołujesz `Update` dla nowego rekordu:

- Jeśli sterownik ODBC obsługuje `::SQLSetPos` funkcji interfejsu API ODBC i MFC używa funkcji, aby dodać rekord w źródle danych. Za pomocą `::SQLSetPos`, MFC można dodać rekord wydajniej, ponieważ nie ma do tworzenia i przetwarzania instrukcji języka SQL.

- Jeśli `::SQLSetPos` nie może być używany, MFC wykonuje następujące czynności:

   1. Jeśli nie wykryto żadnych zmian, `Update` nic nie robi i zwraca wartość 0.

   1. W przypadku zmian, `Update` konstrukcji SQL **Wstaw** instrukcji. Kolumny, reprezentowane przez wszystkie elementy członkowskie danych pola zanieczyszczeniu są wymienione w **Wstaw** instrukcji. Aby wymusić kolumny do uwzględnienia, należy wywołać [SetFieldDirty](../../mfc/reference/crecordset-class.md#setfielddirty) funkcja elementu członkowskiego:

        ```cpp
        SetFieldDirty( &m_dataMember, TRUE );
        ```

   1. `Update` zatwierdza nowy rekord — **Wstaw** zostaje wykonana instrukcja i rekord jest zaangażowana w tabeli w źródle danych (i zestawu rekordów, jeśli nie migawki), chyba że transakcja jest w toku.

   1. Po przywróceniu rekordów przechowywanych w buforze edycji. Rekord, który były aktualne przed `AddNew` wywołanie jest bieżącym ponownie niezależnie od tego, czy **Wstaw** pomyślnie wykonano instrukcję.

   > [!TIP]
   > Aby uzyskać pełną kontrolę nad nowy rekord, wykonaj następujące podejście: Ustaw wartości wszystkich pól, które będą mieć wartości i jawnie ustawić wszystkie pola, które pozostaną o wartości Null, wywołując `SetFieldNull` za pomocą wskaźnika do pola i parametr TRUE (ustawienie domyślne). Jeśli chcesz upewnić się, że pola są one zapisywane do źródła danych, wywołanie `SetFieldDirty` za pomocą wskaźnika do pola i wartość FALSE, parametr i nie należy modyfikować wartości pola. Aby ustalić, czy pole może mieć wartości Null, należy wywołać `IsFieldNullable`.

   > [!TIP]
   > Aby wykryć, kiedy zestaw rekordów składowe danych, zmień wartość, MFC wykorzystuje wartość PSEUDO_NULL odpowiednią dla każdego typu danych, które mogą być przechowywane w zestawie rekordów. Jeśli musisz jawnie ustawić wartość PSEUDO_NULL pola, a pole się zmieni dla już być oznaczone Null, musisz również wywołać `SetFieldNull`, przekazując adres pola pierwszy parametr i wartość FALSE w drugim parametrze.

##  <a name="_core_visibility_of_added_records"></a> Widoczność dodano rekordów

Jeśli dodano rekord jest widoczny dla rekordów? Dodano rekordów czasami widoczne i czasami nie są widoczne, w zależności od dwie rzeczy:

- Jakie sterownika jest w stanie.

- Jakiej platformy, jak korzystać z zalet.

Jeśli sterownik ODBC obsługuje `::SQLSetPos` funkcji interfejsu API ODBC i MFC używa funkcji, aby dodać rekordy. Za pomocą `::SQLSetPos`, dodać rekordy są widoczne dla żadnych nadaje się do aktualizacji rekordów MFC. Bez obsługi funkcji, dodawany rekordy nie są widoczne, a następnie należy wywołać `Requery` widoczne. Za pomocą `::SQLSetPos` również jest bardziej wydajne.

##  <a name="_core_editing_an_existing_record"></a> Edytowanie istniejącego rekordu

Edytowanie istniejącego rekordu w zestawie rekordów obejmuje przewinięcie do rekordu, wywoływanie w zestawie rekordów [Edytuj](../../mfc/reference/crecordset-class.md#edit) funkcji członkowskiej, ustawianie wartości elementów członkowskich danych pola nowego rekordu i wywoływania [aktualizacji](../../mfc/reference/crecordset-class.md#update)funkcja elementu członkowskiego, aby zapisać zmienionych rekordów do źródła danych.

Jako warunek wstępny do wywoływania `Edit`, zestaw rekordów musi być nadaje się do aktualizacji i rekord. `CanUpdate` i `IsDeleted` funkcje Członkowskie pozwalają na określenie tych warunków. Bieżącego rekordu również musi nie już zostały usunięte, a musi być rekordów w zestawie rekordów (zarówno `IsBOF` i `IsEOF` zwracają 0).

Gdy wywołujesz `Edit`, znajduje się rekord w buforze edycji (bieżącego rekordu). Wartości rekordu przechowywanych później są używane do wykrywania, czy wszystkie pola zostały zmienione.

Po wywołaniu metody `Edit`, bufor edycji nadal reprezentuje bieżącego rekordu, ale jest teraz gotowy do przyjęcia zmian elementy członkowskie danych pola. Aby zmienić rekord, ręcznie ustawić wartości wszystkie elementy członkowskie danych pola, który chcesz edytować. Zamiast określania rzeczywista wartość danych dla pola, można wywołać `SetFieldNull` określić wartość Null. Aby zatwierdzić zmiany, należy wywołać `Update`.

> [!TIP]
> Aby uzyskać z `AddNew` lub `Edit` tryb, wywołanie `Move` z parametrem *AFX_MOVE_REFRESH*.

Jako warunek wstępny do wywoływania `Update`bieżącego rekordu nie musiały zostać usunięte i zestawu rekordów nie może być pusta. `IsBOF`, `IsEOF`, i `IsDeleted` powinna zwrócić 0.

Gdy wywołujesz `Update` edytowany rekord:

- Jeśli sterownik ODBC obsługuje `::SQLSetPos` funkcji interfejsu API ODBC i MFC za pomocą funkcji aktualizacji rekordu w źródle danych. Za pomocą `::SQLSetPos`, sterownik porównuje usługi buforu edycji za pomocą odpowiedniego rekordu na serwerze, aktualizuje rekord na serwerze, jeśli dwa są różne. Za pomocą `::SQLSetPos`, MFC można zaktualizować rekord wydajniej, ponieważ nie ma do tworzenia i przetwarzania instrukcji języka SQL.

   \- lub —

- Jeśli `::SQLSetPos` nie może być używany, MFC wykonuje następujące czynności:

   1. Jeśli nie było żadnych zmian `Update` nic nie robi i zwraca wartość 0.

   1. W przypadku zmian, `Update` konstrukcji SQL **aktualizacji** instrukcji. Kolumn na liście **aktualizacji** instrukcji opierają się na elementy członkowskie danych pola, które uległy zmianie.

   1. `Update` zatwierdza zmiany — wykonuje **aktualizacji** instrukcji — rekord zostało zmienione w źródle danych, ale nie zatwierdzone Jeśli transakcja jest w toku (zobacz [transakcja: wykonywanie transakcji w zestawie rekordów (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md) uzyskać informacji na temat wpływ transakcji aktualizacji). ODBC przechowuje kopię rekord, który zmienia także.

   1. W przeciwieństwie do procesu `AddNew`, `Edit` proces nie powoduje przywrócenia rekordów przechowywanych. Edytowany rekord pozostaje w miejscu jako bieżącego rekordu.

   > [!CAUTION]
   > Po przygotowaniu zaktualizuj zestaw rekordów, wywołując `Update`, zajmie się, że rekordów zawiera wszystkich kolumn tworzących klucza podstawowego tabeli (lub wszystkie kolumny wszelkie unikatowego indeksu dla tabeli lub za mało kolumn, do jednoznacznego identyfikowania wiersza). W niektórych przypadkach ramach służy tylko do kolumn, które zostały wybrane w twoim zestawie rekordów do zidentyfikować rekordy w tabeli, aby zaktualizować. Nie wszystkie niezbędne kolumny wielu rekordów mogły zostać zaktualizowane w tabeli. W tym przypadku ramach zgłasza wyjątki podczas wywoływania `Update`.

   > [!TIP]
   > Jeśli wywołasz `AddNew` lub `Edit` po wywołaniu jednej z tych funkcji wcześniej, ale zanim zajdzie wywołania `Update`, bufor edycji zostaną odświeżone przy użyciu przechowywanych rekordu, zastępując rekordu nowe lub zmodyfikowane w toku. To zachowanie umożliwia przerwania `AddNew` lub `Edit` i rozpocząć nową: Jeśli okaże się, że rekord postęp jest uszkodzony, wystarczy wywołać `Edit` lub `AddNew` ponownie.

##  <a name="_core_deleting_a_record"></a> Usuwanie rekordu

Usuwanie rekordu z zestawu rekordów obejmuje przewijanie do rekordu i wywoływanie w zestawie rekordów [Usuń](../../mfc/reference/crecordset-class.md#delete) funkcja elementu członkowskiego. W odróżnieniu od `AddNew` i `Edit`, `Delete` nie wymaga pasujących wywołanie `Update`.

Jako warunek wstępny do wywoływania `Delete`, zestaw rekordów musi zostać nadaje się do aktualizacji, a musi być rekord. `CanUpdate`, `IsBOF`, `IsEOF`, I `IsDeleted` funkcje Członkowskie pozwalają na określenie tych warunków.

Gdy wywołujesz `Delete`:

- Jeśli sterownik ODBC obsługuje `::SQLSetPos` funkcji interfejsu API ODBC i MFC używa funkcji, aby usunąć rekord w źródle danych. Za pomocą `::SQLSetPos` jest zazwyczaj bardziej efektywne niż przy użyciu języka SQL.

   \- lub —

- Jeśli `::SQLSetPos` nie może być używany, MFC wykonuje następujące czynności:

   1. Bieżący rekord w buforze Edycja nie jest obsługiwane jako w `AddNew` i `Edit`.

   1. `Delete` konstruuje SQL **Usuń** instrukcję, która usuwa rekord.

      Bieżący rekord w buforze edycji nie są przechowywane jako w `AddNew` i `Edit`.

   1. `Delete` usuwanie zatwierdzenia — wykonuje **Usuń** instrukcji. Rekord oznaczony usuniętych w źródle danych i, jeśli rekord jest migawką, w ODBC.

   1. Usuniętego rekordu wartości wciąż znajdują się w elementy członkowskie danych pola zestawu rekordów, ale elementy członkowskie danych pola są oznaczone Null i zestawu rekordów `IsDeleted` funkcja elementu członkowskiego zwraca wartość różną od zera.

   > [!NOTE]
   > Po usunięciu rekordu, powinien przewiń do innego rekordu uzupełnienie buforu edycji danych nowy rekord. Jest to błąd, aby wywołać `Delete` ponownie lub wywołać `Edit`.

Aby uzyskać informacji na temat instrukcji SQL używane podczas operacji aktualizacji, zobacz [SQL](../../data/odbc/sql.md).

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: więcej informacji o aktualizacjach (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)<br/>
[Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md)