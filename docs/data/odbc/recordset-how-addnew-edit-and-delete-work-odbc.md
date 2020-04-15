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
ms.openlocfilehash: 63718a6be3a9ce19ddbce923a84def21448c42a0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367005"
---
# <a name="recordset-how-addnew-edit-and-delete-work-odbc"></a>Zestaw rekordów: jak działają funkcje AddNew, Edit i Delete (ODBC)

Ten temat dotyczy klas MFC ODBC.

W tym temacie `AddNew` `Edit`wyjaśniono, jak działają funkcje , i `Delete` element członkowski klasy. `CRecordset` Omawiane tematy to m.in.:

- [Jak działa dodawanie rekordów](#_core_adding_a_record)

- [Widoczność dodanych rekordów](#_core_visibility_of_added_records)

- [Jak działa edytowanie rekordów](#_core_editing_an_existing_record)

- [Jak działa usuwanie rekordów](#_core_deleting_a_record)

> [!NOTE]
> Ten temat dotyczy obiektów pochodzących z `CRecordset` których pobieranie wiersza zbiorczego nie zostało zaimplementowane. Jeśli korzystasz z pobierania wierszy zbiorczych, zobacz [Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Jako dodatek można przeczytać [Record Field Exchange: How RFX Works](../../data/odbc/record-field-exchange-how-rfx-works.md), który opisuje odpowiednią rolę RFX w operacjach aktualizacji.

## <a name="adding-a-record"></a><a name="_core_adding_a_record"></a>Dodawanie rekordu

Dodawanie nowego rekordu do zestawu rekordów polega na wywołaniu funkcji [AddNew](../../mfc/reference/crecordset-class.md#addnew) elementu członkowskiego zbioru rekordów, ustawieniu wartości elementów członkowskich danych pola nowego rekordu i wywołaniu funkcji Aktualizuj element [członkowski](../../mfc/reference/crecordset-class.md#update) w celu zapisania rekordu w źródle danych.

Jako warunek wstępny wywołania, `AddNew`rekord nie może być otwarty jako tylko do odczytu. `CanUpdate` Funkcje `CanAppend` i element członkowski umożliwiają określenie tych warunków.

Kiedy dzwonisz: `AddNew`

- Rekord w buforze edycji jest przechowywany, więc jego zawartość można przywrócić, jeśli operacja zostanie anulowana.

- Elementy członkowskie danych pól są oflagowane, dzięki czemu można wykryć zmiany w nich później. Elementy członkowskie danych pola są również oznaczone jako czyste (niezmienione) i ustawione na Null.

Po wywołaniu `AddNew`bufor edycji reprezentuje nowy, pusty rekord, gotowy do wypełnienia wartościami. Aby to zrobić, należy ręcznie ustawić wartości, przypisując do nich. Zamiast określać rzeczywistą wartość danych dla pola, `SetFieldNull` można wywołać, aby określić wartość Null.

Aby zatwierdzić zmiany, `Update`należy wywołać . Po wywołaniu `Update` nowego rekordu:

- Jeśli sterownik ODBC `::SQLSetPos` obsługuje funkcję INTERFEJSU API ODBC, MFC używa tej funkcji do dodania rekordu w źródle danych. Z `::SQLSetPos`, MFC można dodać rekord bardziej efektywnie, ponieważ nie trzeba konstruować i przetwarzać instrukcji SQL.

- Jeśli `::SQLSetPos` nie można użyć, MFC wykonuje następujące czynności:

   1. Jeśli żadne zmiany nie `Update` zostaną wykryte, nic nie robi i zwraca wartość 0.

   1. Jeśli są zmiany, `Update` konstruuje instrukcję SQL **INSERT.** Kolumny reprezentowane przez wszystkie elementy członkowskie danych pola zanieczyszczonego są wymienione w instrukcji **INSERT.** Aby wymusić uwzględnienie kolumny, należy wywołać funkcję elementu członkowskiego [SetFieldDirty:](../../mfc/reference/crecordset-class.md#setfielddirty)

        ```cpp
        SetFieldDirty( &m_dataMember, TRUE );
        ```

   1. `Update`zatwierdza nowy rekord — instrukcja **INSERT** jest wykonywana, a rekord jest zatwierdzony do tabeli w źródle danych (i zestawie rekordów, jeśli nie migawka), chyba że transakcja jest w toku.

   1. Przechowywany rekord zostanie przywrócony do buforu edycji. Rekord, który był `AddNew` aktualny przed wywołaniem jest ponownie bieżący, niezależnie od tego, czy instrukcja **INSERT** została pomyślnie wykonana.

   > [!TIP]
   > Aby uzyskać pełną kontrolę nad nowym rekordem, należy przyjąć następujące podejście: ustawić wartości wszystkich pól, które `SetFieldNull` będą miały wartości, a następnie jawnie ustawić wszystkie pola, które pozostaną null, wywołując ze wskaźnikiem do pola i parametru TRUE (domyślnie). Jeśli chcesz upewnić się, że pole nie jest `SetFieldDirty` zapisywane w źródle danych, wywołaj ze wskaźnikiem do pola i parametrem FALSE i nie modyfikuj wartości pola. Aby ustalić, czy pole może być `IsFieldNullable`null, wywołać .

   > [!TIP]
   > Aby wykryć, kiedy elementy członkowskie danych zestawu rekordów zmienić wartość, MFC używa PSEUDO_NULL wartość odpowiednią dla każdego typu danych, które można przechowywać w pliku recordset. Jeśli pole musi jawnie ustawić wartość PSEUDO_NULL, a pole ma już oznaczenie Null, `SetFieldNull`należy również wywołać , przekazując adres pola w pierwszym parametrze i FAŁSZ w drugim parametrze.

## <a name="visibility-of-added-records"></a><a name="_core_visibility_of_added_records"></a>Widoczność dodanych rekordów

Kiedy dodatkowy rekord jest widoczny dla twojego rekordu? Dodane rekordy czasami pojawiają się, a czasami nie są widoczne, w zależności od dwóch rzeczy:

- Do czego zdolny jest twój kierowca.

- Z czego mogą korzystać ramy.

Jeśli sterownik ODBC `::SQLSetPos` obsługuje funkcję INTERFEJSU API ODBC, MFC używa tej funkcji do dodawania rekordów. Z `::SQLSetPos`, dodane rekordy są widoczne dla wszystkich aktualizacji MFC recordset. Bez obsługi funkcji dodane rekordy nie są widoczne `Requery` i należy wywołać, aby je zobaczyć. Korzystanie `::SQLSetPos` jest również bardziej wydajne.

## <a name="editing-an-existing-record"></a><a name="_core_editing_an_existing_record"></a>Edytowanie istniejącego rekordu

Edytowanie istniejącego rekordu w liście rekordów polega na przewijaniu do rekordu, wywoływaniu funkcji [edytuj](../../mfc/reference/crecordset-class.md#edit) elementu członkowskiego zestawu rekordów, ustawianiu wartości elementów członkowskich danych pola nowego rekordu i wywoływaniu funkcji Aktualizuj element [członkowski](../../mfc/reference/crecordset-class.md#update) w celu zapisania zmienionego rekordu w źródle danych.

Jako warunek wstępny wywoływania, `Edit`plik rekordów musi być aktualizowany i zapisywany. `CanUpdate` Funkcje `IsDeleted` i element członkowski umożliwiają określenie tych warunków. Bieżący rekord również nie może już zostać usunięty, a w `IsBOF` gosi musi znajdować się rekordy (oba i `IsEOF` zwracaj 0).

Podczas wywoływania `Edit`rekord w buforze edycji (bieżący rekord) jest przechowywany. Wartości przechowywanego rekordu są później używane do wykrywania, czy pola zostały zmienione.

Po wywołaniu `Edit`bufor edycji nadal reprezentuje bieżący rekord, ale jest teraz gotowy do zaakceptowania zmian w elementach członkowskich danych pola. Aby zmienić rekord, należy ręcznie ustawić wartości wszystkich elementów członkowskich danych pola, które mają być edytowane. Zamiast określać rzeczywistą wartość danych dla pola, `SetFieldNull` można wywołać, aby określić wartość Null. Aby zatwierdzić zmiany, zadzwoń do . `Update`

> [!TIP]
> Aby wyjść `AddNew` z `Edit` trybu `Move` lub tryb, zadzwoń z parametrem *AFX_MOVE_REFRESH*.

Jako warunek wstępny wywołania, `Update`grupa rekordów nie może być pusta, a bieżący rekord nie może zostać usunięty. `IsBOF`, `IsEOF`i `IsDeleted` powinny wszystkie zwrócić 0.

Po wywołaniu `Update` edytowany rekord:

- Jeśli sterownik ODBC `::SQLSetPos` obsługuje funkcję INTERFEJSU API ODBC, MFC używa tej funkcji do aktualizowania rekordu w źródle danych. W `::SQLSetPos`programie sterownik porównuje bufor edycji z odpowiednim rekordem na serwerze, aktualizując rekord na serwerze, jeśli oba są różne. Z `::SQLSetPos`, MFC można zaktualizować rekord bardziej efektywnie, ponieważ nie trzeba konstruować i przetwarzać instrukcji SQL.

   \-lub -

- Jeśli `::SQLSetPos` nie można użyć, MFC wykonuje następujące czynności:

   1. Jeśli nie było żadnych `Update` zmian, nie robi nic i zwraca 0.

   1. Jeśli są zmiany, `Update` konstruuje instrukcję SQL **UPDATE.** Kolumny wymienione w instrukcji **UPDATE** są oparte na elementach członkowskich danych pola, które uległy zmianie.

   1. `Update`zatwierdza zmiany — wykonuje **update** instrukcji — i rekord jest zmieniany w źródle danych, ale nie zatwierdzone, jeśli transakcja jest w toku (zobacz [Transakcja: Wykonywanie transakcji w Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md) informacji o tym, jak transakcja wpływa na aktualizację). ODBC przechowuje kopię rekordu, który również się zmienia.

   1. W przeciwieństwie `AddNew`do `Edit` procesu , proces nie przywraca przechowywanego rekordu. Edytowany rekord pozostaje w miejscu jako bieżący rekord.

   > [!CAUTION]
   > Podczas przygotowywania do aktualizacji zestawie `Update`rekordów przez wywołanie, należy zadbać, aby zestaw rekordów zawiera wszystkie kolumny składające się na klucz podstawowy tabeli (lub wszystkie kolumny dowolnego unikatowego indeksu w tabeli lub wystarczającej liczby kolumn, aby jednoznacznie zidentyfikować wiersz). W niektórych przypadkach struktura może używać tylko kolumn wybranych w zakuli rekordów, aby zidentyfikować rekord w tabeli do aktualizacji. Bez wszystkich niezbędnych kolumn wiele rekordów może zostać zaktualizowanych w tabeli. W takim przypadku struktura zgłasza wyjątki `Update`podczas wywoływania .

   > [!TIP]
   > Jeśli `AddNew` wywołasz `Edit` lub po wywołaniu jednej funkcji `Update`wcześniej, ale przed wywołaniem, bufor edycji zostanie odświeżony z zapisanym rekordem, zastępując nowy lub edytowany rekord w toku. To zachowanie daje sposób, aby `AddNew` `Edit` przerwać lub rozpocząć nowy: jeśli stwierdzisz, że rekord `Edit` w `AddNew` toku jest uszkodzony, po prostu wywołać lub ponownie.

## <a name="deleting-a-record"></a><a name="_core_deleting_a_record"></a>Usuwanie rekordu

Usunięcie rekordu z pliku recordset polega na przewinięciu do rekordu i wywołaniu funkcji Usuń element członkowski w [uchwale.](../../mfc/reference/crecordset-class.md#delete) W `AddNew` `Edit`przeciwieństwie `Delete` do i , `Update`nie wymaga pasującego wywołania do .

Jako warunek wstępny wywoływania, `Delete`plik rekordów musi być aktualizowany i musi być zapisywany. `CanUpdate`Funkcje `IsBOF` `IsEOF`, `IsDeleted` i element członkowski umożliwiają określenie tych warunków.

Kiedy dzwonisz: `Delete`

- Jeśli sterownik ODBC `::SQLSetPos` obsługuje funkcję INTERFEJSU API ODBC, MFC używa tej funkcji do usunięcia rekordu ze źródła danych. Korzystanie `::SQLSetPos` jest zwykle bardziej wydajne niż przy użyciu języka SQL.

   \-lub -

- Jeśli `::SQLSetPos` nie można użyć, MFC wykonuje następujące czynności:

   1. Kopia zapasowa bieżącego rekordu w buforze edycji nie jest archiwizowana jako in `AddNew` i `Edit`.

   1. `Delete`tworzy instrukcję SQL **DELETE,** która usuwa rekord.

      Bieżący rekord w buforze edycji `AddNew` `Edit`nie jest przechowywany jako in i .

   1. `Delete`zatwierdza usunięcie — wykonuje instrukcję **DELETE.** Rekord jest oznaczony jako usunięty w źródle danych, a jeśli rekord jest migawką, w odbc.

   1. Wartości usuniętego rekordu są nadal w elementach członkowskich danych pola zbioru rekordów, ale elementy `IsDeleted` członkowskie danych pola są oznaczone jako Null, a funkcja elementu członkowskiego zbioru rekordów zwraca wartość niezerową.

   > [!NOTE]
   > Po usunięciu rekordu należy przewinąć do innego rekordu, aby uzupełnić bufor edycji danymi nowego rekordu. Jest to błąd, `Delete` aby zadzwonić ponownie lub zadzwonić `Edit`.

Aby uzyskać informacje na temat instrukcji SQL używanych w operacjach aktualizacji, zobacz [SQL](../../data/odbc/sql.md).

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: więcej informacji o aktualizacjach (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)<br/>
[Wymiana pól rekordu (RFX)](../../data/odbc/record-field-exchange-rfx.md)
