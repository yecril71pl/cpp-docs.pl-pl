---
title: 'Zestaw rekordów: dodawanie, aktualizowanie i usuwanie rekordów (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- records [C++], updating
- record editing [C++], in recordsets
- recordsets [C++], adding records
- records [C++], adding
- ODBC recordsets [C++], adding records
- recordsets [C++], editing records
- recordsets [C++], updating
- records [C++], deleting
- AddNew method
- ODBC recordsets [C++], deleting records
- data in recordsets [C++]
- record editing [C++]
- recordsets [C++], deleting records
- ODBC recordsets [C++], editing records
- records [C++], editing
ms.assetid: 760c8889-bec4-482b-a8f2-319792a6af98
ms.openlocfilehash: 628ffb2feee385a4114b0dbea074f81678c529d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367106"
---
# <a name="recordset-adding-updating-and-deleting-records-odbc"></a>Zestaw rekordów: dodawanie, aktualizowanie i usuwanie rekordów (ODBC)

Ten temat dotyczy klas MFC ODBC.

> [!NOTE]
> Teraz można dodawać rekordy zbiorczo bardziej efektywnie. Aby uzyskać więcej informacji, zobacz [Recordset: Dodawanie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-adding-records-in-bulk-odbc.md).

> [!NOTE]
> Ten temat dotyczy obiektów pochodzących z `CRecordset` których pobieranie wiersza zbiorczego nie zostało zaimplementowane. Jeśli korzystasz z pobierania wierszy zbiorczych, zobacz [Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Można aktualizować migawki i zestawy dynasetów umożliwiają dodawanie, edytowanie (aktualizowanie) i usuwanie rekordów. W tym temacie wyjaśniono:

- [Jak ustalić, czy plik recordset można aktualizować](#_core_determining_whether_your_recordset_is_updatable).

- [Jak dodać nowy rekord](#_core_adding_a_record_to_a_recordset).

- [Jak edytować istniejący rekord](#_core_editing_a_record_in_a_recordset).

- [Jak usunąć rekord](#_core_deleting_a_record_from_a_recordset).

Aby uzyskać więcej informacji o sposobie przeprowadzania aktualizacji i sposobie pojawiania się aktualizacji innym użytkownikom, zobacz [Recordset: How Recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md). Zwykle po dodaniu, edycji lub usunięciu rekordu zestaw rekordów natychmiast zmienia źródło danych. Zamiast tego można grup wsadowych powiązanych aktualizacji do transakcji. Jeśli transakcja jest w toku, aktualizacja nie staje się ostateczna, dopóki nie zatwierdzisz transakcji. Dzięki temu można cofnąć lub wycofać zmiany. Aby uzyskać informacje o transakcjach, zobacz [Transakcja (ODBC)](../../data/odbc/transaction-odbc.md).

W poniższej tabeli podsumowano opcje dostępne dla zestawy rekordów o różnych cechach aktualizacji.

### <a name="recordset-readupdate-options"></a>Opcje odczytu/aktualizacji wachcie/aktualizacji wachcie rekordów

|Typ|Odczyt|Edycja rekordu|Usuwanie rekordu|Dodaj nowy (dołącz)|
|----------|----------|-----------------|-------------------|------------------------|
|Tylko odczyt|Tak|Nie|Nie|Nie|
|Tylko do dołączania|Tak|Nie|Nie|Tak|
|W pełni aktualizowane|Tak|Tak|Tak|Tak|

## <a name="determining-whether-your-recordset-is-updateable"></a><a name="_core_determining_whether_your_recordset_is_updatable"></a>Określanie, czy twój rekord jest aktualizowany

Obiekt zestawu rekordów można aktualizować, jeśli źródło danych można aktualizować i otworzyć zestaw rekordów jako można go zaktualizować. Jego możliwość aktualizacji zależy również od instrukcji SQL, której używasz, możliwości sterownika ODBC i od tego, czy biblioteka kursora ODBC znajduje się w pamięci. Nie można zaktualizować zbioru rekordów tylko do odczytu ani źródła danych.

#### <a name="to-determine-whether-your-recordset-is-updatable"></a>Aby ustalić, czy można aktualizować swój rekord

1. Wywołanie funkcji elementu członkowskiego [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) obiektu pliku records.

   `CanUpdate`zwraca wartość niezerową, jeśli jest można zaktualizować.

Domyślnie zestawy rekordów można w pełni `AddNew` `Edit`aktualizować `Delete` (można wykonywać programy i operacje). Ale można również użyć opcji [appendOnly,](../../mfc/reference/crecordset-class.md#open) aby otworzyć aktualizowane zestawy rekordów. Rekord otwarty w ten sposób pozwala tylko `AddNew`na dodanie nowych rekordów z . Nie można edytować ani usuwać istniejących rekordów. Można sprawdzić, czy plik recordset jest otwarty tylko do dołączania, wywołując funkcję elementu członkowskiego [CanAppend.](../../mfc/reference/crecordset-class.md#canappend) `CanAppend`zwraca wartość niezerową, jeśli plik recordset jest w pełni aktualizowany lub otwierany tylko do dołączania.

Poniższy kod pokazuje, `CanUpdate` jak można użyć `rsStudentSet`dla obiektu akcesji o nazwie:

```cpp
if( !rsStudentSet.Open( ) )
    return FALSE;
if( !rsStudentSet.CanUpdate( ) )
{
    AfxMessageBox( "Unable to update the Student recordset." );
    return;
}
```

> [!CAUTION]
> Podczas przygotowywania do aktualizacji zestawie `Update`rekordów przez wywołanie, należy zadbać, aby zestaw rekordów zawiera wszystkie kolumny składające się na klucz podstawowy tabeli (lub wszystkie kolumny dowolnego unikatowego indeksu w tabeli). W niektórych przypadkach struktura może używać tylko kolumn wybranych w zakuli rekordów, aby zidentyfikować rekord w tabeli do aktualizacji. Bez wszystkich niezbędnych kolumn wiele rekordów może zostać zaktualizowanych w tabeli, co może uszkodzić więzy integralności tabeli. W takim przypadku struktura zgłasza wyjątki `Update`podczas wywoływania .

## <a name="adding-a-record-to-a-recordset"></a><a name="_core_adding_a_record_to_a_recordset"></a>Dodawanie rekordu do a recordset

Można dodać nowe rekordy do pliku recordset, jeśli jego funkcja elementu członkowskiego [CanAppend](../../mfc/reference/crecordset-class.md#canappend) zwraca wartość niezerową.

#### <a name="to-add-a-new-record-to-a-recordset"></a>Aby dodać nowy rekord do akcesu

1. Upewnij się, że plik recordset jest dołączany.

1. Wywołanie funkcji [AddNew](../../mfc/reference/crecordset-class.md#addnew) elementu członkowskiego obiektu pliku recordset.

   `AddNew`przygotowuje plik recordset do działania jako bufor edycji. Wszystkie elementy członkowskie danych pola są ustawione na wartość specjalną Null i oznaczone jako niezmienione, więc tylko zmienione (zabrudzone) wartości są zapisywane w źródle danych podczas [wywoływania update](../../mfc/reference/crecordset-class.md#update).

1. Ustaw wartości elementów członkowskich danych pola nowego rekordu.

   Przypisywanie wartości do elementów członkowskich danych pola. Te, które nie zostały przypisane, nie są zapisywane w źródle danych.

1. Wywołanie funkcji `Update` elementu członkowskiego obiektu pliku recordset.

   `Update`kończy dodawanie, zapisując nowy rekord w źródle danych. Aby uzyskać informacje o tym, że nie można wywołać połączenia, `Update`zobacz [Tablica rekordów: Jak recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

Aby uzyskać informacje o tym, jak działa dodawanie rekordów i o tym, kiedy dodane rekordy są widoczne w tablicy rekordów, zobacz [Tablica rekordów: Jak dodać nowe, edytuj i usuwać pracę (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md).

W poniższym przykładzie pokazano, jak dodać nowy rekord:

```cpp
if( !rsStudent.Open( ) )
    return FALSE;
if( !rsStudent.CanAppend( ) )
    return FALSE;                      // no field values were set
rsStudent.AddNew( );
rsStudent.m_strName = strName;
rsStudent.m_strCity = strCity;
rsStudent.m_strStreet = strStreet;
if( !rsStudent.Update( ) )
{
    AfxMessageBox( "Record not added; no field values were set." );
    return FALSE;
}
```

> [!TIP]
> `AddNew` Aby anulować `Edit` lub zadzwonić, `AddNew` po `Edit` prostu `Move` nawiązać połączenie lub zadzwonić z *parametrem AFX_MOVE_REFRESH.* Elementy członkowskie danych są resetowane do `Edit` ich `Add` poprzednich wartości i nadal jesteś w trybie.

## <a name="editing-a-record-in-a-recordset"></a><a name="_core_editing_a_record_in_a_recordset"></a>Edytowanie rekordu w a recordset

Można edytować istniejące rekordy, jeśli funkcja elementu członkowskiego [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) w zestawie rekordów zwraca wartość niezerową.

#### <a name="to-edit-an-existing-record-in-a-recordset"></a>Aby edytować istniejący rekord w ustawie rekordzie

1. Upewnij się, że plik recordset można zaktualizować.

1. Przewiń do rekordu, który chcesz zaktualizować.

1. Wywołanie funkcji [edytuj](../../mfc/reference/crecordset-class.md#edit) elementu członkowskiego obiektu pliku recordset.

   `Edit`przygotowuje plik recordset do działania jako bufor edycji. Wszystkie elementy członkowskie danych pól są oznaczone, dzięki czemu zestaw rekordów może później stwierdzić, czy zostały zmienione. Nowe wartości dla zmienionych elementów członkowskich danych pól są zapisywane w źródle danych podczas [wywoływania update](../../mfc/reference/crecordset-class.md#update).

1. Ustaw wartości elementów członkowskich danych pola nowego rekordu.

   Przypisywanie wartości do elementów członkowskich danych pola. Te, które nie są przypisywane wartości pozostają niezmienione.

1. Wywołanie funkcji `Update` elementu członkowskiego obiektu pliku recordset.

   `Update`kończy edycję, zapisując zmieniony rekord w źródle danych. Aby uzyskać informacje o tym, że nie można wywołać połączenia, `Update`zobacz [Tablica rekordów: Jak recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

Po edycji rekordu edytowany rekord pozostaje bieżącym rekordem.

W poniższym `Edit` przykładzie przedstawiono operację. Zakłada się, że użytkownik został przeniesiony do rekordu, który chce edytować.

```cpp
rsStudent.Edit( );
rsStudent.m_strStreet = strNewStreet;
rsStudent.m_strCity = strNewCity;
rsStudent.m_strState = strNewState;
rsStudent.m_strPostalCode = strNewPostalCode;
if( !rsStudent.Update( ) )
{
    AfxMessageBox( "Record not updated; no field values were set." );
    return FALSE;
}
```

> [!TIP]
> `AddNew` Aby anulować `Edit` lub zadzwonić, `AddNew` po `Edit` prostu `Move` nawiązać połączenie lub zadzwonić z *parametrem AFX_MOVE_REFRESH.* Elementy członkowskie danych są resetowane do `Edit` ich `Add` poprzednich wartości i nadal jesteś w trybie.

## <a name="deleting-a-record-from-a-recordset"></a><a name="_core_deleting_a_record_from_a_recordset"></a>Usuwanie rekordu z rekordu z rekordu

Można usunąć rekordy, jeśli funkcja elementu członkowskiego [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) w zestawie rekordów zwraca wartość niezerową.

#### <a name="to-delete-a-record"></a>Aby usunąć rekord

1. Upewnij się, że plik recordset można zaktualizować.

1. Przewiń do rekordu, który chcesz zaktualizować.

1. Wywołanie funkcji Usuń element [członkowski](../../mfc/reference/crecordset-class.md#delete) obiektu.

   `Delete`natychmiast oznacza rekord jako usunięty, zarówno w zbiorze rekordów, jak i w źródle danych.

   W `AddNew` `Edit`przeciwieństwie `Delete` do `Update` i , nie ma odpowiedniego połączenia.

1. Przewiń do innego rekordu.

   > [!NOTE]
   >  Podczas przechodzenia przez plan rekordów usunięte rekordy mogą nie zostać pominięte. Aby uzyskać więcej informacji, zobacz [IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted) funkcji elementu członkowskiego.

W poniższym `Delete` przykładzie przedstawiono operację. Przyjęto założenie, że użytkownik został przeniesiony do rekordu, który użytkownik chce usunąć. Po `Delete` wywołaniu ważne jest, aby przejść do nowego rekordu.

```
rsStudent.Delete( );
rsStudent.MoveNext( );
```

Aby uzyskać więcej informacji `AddNew`na `Edit`temat `Delete` efektów funkcji programu , i członków, zobacz [Recordset: How Recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: blokowanie rekordów (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
