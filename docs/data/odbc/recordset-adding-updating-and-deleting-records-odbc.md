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
ms.openlocfilehash: 14fc26709541135e80a2e0fe4de872cc75221874
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213008"
---
# <a name="recordset-adding-updating-and-deleting-records-odbc"></a>Zestaw rekordów: dodawanie, aktualizowanie i usuwanie rekordów (ODBC)

Ten temat dotyczy klas MFC ODBC.

> [!NOTE]
>  Teraz można bardziej wydajniej dodawać rekordy. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: zbiorcze Dodawanie rekordów (ODBC)](../../data/odbc/recordset-adding-records-in-bulk-odbc.md).

> [!NOTE]
>  Ten temat dotyczy obiektów pochodnych `CRecordset`, w których nie zaimplementowano pobierania wierszy zbiorczych. Jeśli używasz pobierania wierszy zbiorczych, zobacz [zestaw rekordów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Możliwe do zaktualizowania migawki i zestawy dynamiczne umożliwiają dodawanie, edytowanie (aktualizowanie) i usuwanie rekordów. W tym temacie objaśniono:

- [Jak ustalić, czy zestaw rekordów jest aktualizowalny](#_core_determining_whether_your_recordset_is_updatable).

- [Jak dodać nowy rekord](#_core_adding_a_record_to_a_recordset).

- [Jak edytować istniejący rekord](#_core_editing_a_record_in_a_recordset).

- [Jak usunąć rekord](#_core_deleting_a_record_from_a_recordset).

Aby uzyskać więcej informacji na temat sposobu przeprowadzania aktualizacji i sposobu, w jaki aktualizacje są widoczne dla innych użytkowników, zobacz [zestaw rekordów: jak zestawy rekordów aktualizują rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md). Zwykle w przypadku dodawania, edytowania lub usuwania rekordu zestaw rekordów natychmiast zmienia źródło danych. Zamiast tego można wsadowo grupy powiązanych aktualizacji do transakcji. Jeśli transakcja jest w toku, aktualizacja nie stanie się końcowa, dopóki nie zostanie zatwierdzona transakcja. Pozwala to cofnąć lub wycofać zmiany. Aby uzyskać informacje o transakcjach, zobacz [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

Poniższa tabela zawiera podsumowanie opcji dostępnych dla zestawów rekordów o różnych właściwościach aktualizacji.

### <a name="recordset-readupdate-options"></a>Opcje odczytywania/aktualizowania zestawu rekordów

|Typ|Odczytywanie|Edytuj rekord|Usuń rekord|Dodaj nowe (Dołącz)|
|----------|----------|-----------------|-------------------|------------------------|
|Tylko do odczytu|Tak|Nie|Nie|Nie|
|Tylko do odczytu|Tak|Nie|Nie|Tak|
|W pełni aktualizowalne|Tak|Tak|Tak|Tak|

##  <a name="determining-whether-your-recordset-is-updateable"></a><a name="_core_determining_whether_your_recordset_is_updatable"></a>Określanie, czy zestaw rekordów jest aktualizowalny

Obiekt zestawu rekordów jest aktualizowalny, jeśli źródło danych jest możliwe do zaktualizowania, a zestaw rekordów został otwarty jako aktualizowalne. Jego możliwość aktualizowania zależy również od używanej instrukcji języka SQL, możliwości sterownika ODBC oraz tego, czy biblioteka kursorów ODBC znajduje się w pamięci. Nie można zaktualizować zestawu rekordów lub źródła danych tylko do odczytu.

#### <a name="to-determine-whether-your-recordset-is-updatable"></a>Aby określić, czy zestaw rekordów jest aktualizowalny

1. Wywołaj funkcję elementu członkowskiego " [Update](../../mfc/reference/crecordset-class.md#canupdate) " obiektu zestawu rekordów.

   `CanUpdate` zwraca wartość różną od zera, jeśli zestaw rekordów jest aktualizowalny.

Domyślnie zestawy rekordów są w pełni aktualizowalne (można wykonywać operacje `AddNew`, `Edit`i `Delete`). Ale można również użyć opcji [AppendOnly](../../mfc/reference/crecordset-class.md#open) , aby otworzyć aktualizowalne zestawy rekordów. Zestaw rekordów otwarty w ten sposób zezwala tylko na dodawanie nowych rekordów z `AddNew`. Nie można edytować ani usuwać istniejących rekordów. Możesz sprawdzić, czy zestaw rekordów jest otwarty tylko do dołączania przez wywołanie funkcji [dołączania](../../mfc/reference/crecordset-class.md#canappend) elementu członkowskiego. `CanAppend` zwraca wartość różną od zera, jeśli zestaw rekordów jest w pełni aktualizowalny lub otwarty tylko do dołączania.

Poniższy kod pokazuje, jak można użyć `CanUpdate` dla obiektu zestawu rekordów o nazwie `rsStudentSet`:

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
>  Podczas przygotowywania do aktualizowania zestawu rekordów przez wywoływanie `Update`należy zwrócić uwagę, że zestaw rekordów zawiera wszystkie kolumny tworzące klucz podstawowy tabeli (lub wszystkie kolumny dowolnego unikatowego indeksu w tabeli). W niektórych przypadkach struktura może używać tylko kolumn wybranych w zestawie rekordów, aby identyfikować, który rekord w tabeli należy zaktualizować. Bez wszystkich wymaganych kolumn w tabeli można zaktualizować wiele rekordów, co może spowodować uszkodzenie integralności referencyjnej tabeli. W takim przypadku platforma zgłasza wyjątki podczas wywoływania `Update`.

##  <a name="adding-a-record-to-a-recordset"></a><a name="_core_adding_a_record_to_a_recordset"></a>Dodawanie rekordu do zestawu rekordów

Nowe rekordy można dodać do zestawu rekordów, jeśli jego funkcja członkowska [dołączania](../../mfc/reference/crecordset-class.md#canappend) zwróci wartość różną od zera.

#### <a name="to-add-a-new-record-to-a-recordset"></a>Aby dodać nowy rekord do zestawu rekordów

1. Upewnij się, że zestaw rekordów jest dołączany.

1. Wywołaj funkcję elementu członkowskiego [AddNew](../../mfc/reference/crecordset-class.md#addnew) obiektu zestawu rekordów.

   `AddNew` przygotowuje zestaw rekordów do działania jako bufor edycji. Wszystkie elementy członkowskie danych pól są ustawione na wartość specjalną o wartości null i oznaczone jako niezmienione, tak aby tylko zmienione (zanieczyszczone) wartości były zapisywane w źródle danych podczas wywoływania [aktualizacji](../../mfc/reference/crecordset-class.md#update).

1. Ustaw wartości elementów członkowskich danych pola nowego rekordu.

   Przypisz wartości do elementów członkowskich danych pola. Te, które nie są przypisane, nie są zapisywane w źródle danych.

1. Wywołaj funkcję członkowską `Update` obiektu zestawu rekordów.

   `Update` uzupełnia Dodawanie, pisząc nowy rekord do źródła danych. Aby uzyskać informacje na temat sytuacji, w której nie można wywołać `Update`, zobacz [zestaw rekordów: jak zestawy rekordów aktualizują rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

Aby uzyskać informacje na temat sposobu działania dodawania rekordów i informacje o tym, kiedy w zestawie rekordów są widoczne dodane rekordy, zobacz [zestaw rekordów: jak AddNew, Edit i DELETE Work (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md).

Poniższy przykład pokazuje, jak dodać nowy rekord:

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
>  Aby anulować wywołanie `AddNew` lub `Edit`, po prostu wykonaj inne wywołanie `AddNew` lub `Edit` lub wywołaj `Move` z parametrem *AFX_MOVE_REFRESH* . Elementy członkowskie danych są resetowane do poprzednich wartości i nadal są w trybie `Edit` lub `Add`.

##  <a name="editing-a-record-in-a-recordset"></a><a name="_core_editing_a_record_in_a_recordset"></a>Edytowanie rekordu w zestawie rekordów

Istniejące rekordy można edytować, jeśli funkcja członkowska [aktualizacji](../../mfc/reference/crecordset-class.md#canupdate) zestawu rekordów zwraca wartość różną od zera.

#### <a name="to-edit-an-existing-record-in-a-recordset"></a>Aby edytować istniejący rekord w zestawie rekordów

1. Upewnij się, że zestaw rekordów jest aktualizowalny.

1. Przewiń do rekordu, który chcesz zaktualizować.

1. Wywołaj funkcję [edycji](../../mfc/reference/crecordset-class.md#edit) elementu członkowskiego obiektu zestawu rekordów.

   `Edit` przygotowuje zestaw rekordów do działania jako bufor edycji. Wszystkie elementy członkowskie danych pola są oznaczone, aby zestaw rekordów mógł później ustalić, czy zostały zmienione. Nowe wartości zmienionych elementów członkowskich danych pola są zapisywane w źródle danych podczas wywoływania [aktualizacji](../../mfc/reference/crecordset-class.md#update).

1. Ustaw wartości elementów członkowskich danych pola nowego rekordu.

   Przypisz wartości do elementów członkowskich danych pola. Te wartości nie są przypisywane.

1. Wywołaj funkcję członkowską `Update` obiektu zestawu rekordów.

   `Update` wykonuje edycję, pisząc zmieniony rekord w źródle danych. Aby uzyskać informacje na temat sytuacji, w której nie można wywołać `Update`, zobacz [zestaw rekordów: jak zestawy rekordów aktualizują rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

Po przeprowadzeniu edycji rekordu edytowany rekord pozostaje bieżącym rekordem.

W poniższym przykładzie pokazano `Edit` operacji. Przyjęto założenie, że użytkownik został przeniesiony do rekordu lub chce go edytować.

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
> Aby anulować wywołanie `AddNew` lub `Edit`, po prostu wykonaj inne wywołanie `AddNew` lub `Edit` lub wywołaj `Move` z parametrem *AFX_MOVE_REFRESH* . Elementy członkowskie danych są resetowane do poprzednich wartości i nadal są w trybie `Edit` lub `Add`.

##  <a name="deleting-a-record-from-a-recordset"></a><a name="_core_deleting_a_record_from_a_recordset"></a>Usuwanie rekordu z zestawu rekordów

Rekordy można usunąć, jeśli funkcja członkowska [aktualizacji](../../mfc/reference/crecordset-class.md#canupdate) zestawu rekordów zwraca wartość różną od zera.

#### <a name="to-delete-a-record"></a>Aby usunąć rekord

1. Upewnij się, że zestaw rekordów jest aktualizowalny.

1. Przewiń do rekordu, który chcesz zaktualizować.

1. Wywołaj funkcję [usuwania](../../mfc/reference/crecordset-class.md#delete) elementu członkowskiego obiektu zestawu rekordów.

   `Delete` natychmiast oznacza rekord jako usunięty, zarówno w zestawie rekordów, jak i w źródle danych.

   W przeciwieństwie do `AddNew` i `Edit``Delete` nie ma odpowiedniego wywołania `Update`.

1. Przewiń do innego rekordu.

   > [!NOTE]
   >  Podczas przechodzenia przez zestaw rekordów usunięte rekordy mogą nie zostać pominięte. Aby uzyskać więcej informacji, zobacz Funkcja elementu członkowskiego [isdelete](../../mfc/reference/crecordset-class.md#isdeleted) .

W poniższym przykładzie pokazano `Delete` operacji. Przyjęto założenie, że użytkownik został przeniesiony do rekordu, który użytkownik chce usunąć. Po wywołaniu `Delete` należy przenieść do nowego rekordu.

```
rsStudent.Delete( );
rsStudent.MoveNext( );
```

Aby uzyskać więcej informacji na temat efektów `AddNew`, `Edit`i `Delete` funkcji Członkowskich, zobacz [zestaw rekordów: jak zestawy rekordów aktualizują rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: blokowanie rekordów (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
