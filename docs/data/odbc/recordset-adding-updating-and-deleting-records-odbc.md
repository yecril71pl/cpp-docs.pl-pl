---
title: 'Zestaw rekordów: Dodawanie, aktualizowanie i usuwanie rekordów (ODBC) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0bdc7e1e5f272ed33423fc0c986459f4b85000d6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062075"
---
# <a name="recordset-adding-updating-and-deleting-records-odbc"></a>Zestaw rekordów: dodawanie, aktualizowanie i usuwanie rekordów (ODBC)

Ten temat dotyczy klas MFC ODBC.  
  
> [!NOTE]
>  Możesz teraz dodać rekordy, w trybie zbiorczym wydajniej. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: dodawanie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-adding-records-in-bulk-odbc.md).  
  
> [!NOTE]
>  Ten temat dotyczy obiektów pochodzących od `CRecordset` w wierszu zbiorczego, które podczas pobierania nie została zaimplementowana. Jeśli używasz zbiorcze pobieranie z wiersza, zobacz [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
Migawki można aktualizować zestawów dynamicznych zezwala na dodawanie, edytowanie (aktualizacja) i usuwania rekordów. W tym temacie opisano:  
  
- [Jak ustalić, czy rekordów nadaje się do](#_core_determining_whether_your_recordset_is_updatable).  
  
- [Jak dodać nowy rekord](#_core_adding_a_record_to_a_recordset).  
  
- [Jak edytować istniejący rekord](#_core_editing_a_record_in_a_recordset).  
  
- [Jak usunąć rekord](#_core_deleting_a_record_from_a_recordset).  
  
Aby uzyskać więcej informacji na temat sposobu aktualizacji są przenoszone poza, a aktualizacje są wyświetlane na innych użytkowników, zobacz [zestaw rekordów: jak zestawy rekordów uaktualniają rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md). Normalnie Jeśli dodawanie, edytowanie lub usuwanie rekordu zestawu rekordów ulega zmianie źródła danych natychmiast. Można zamiast tego partii grupy powiązane aktualizacje na transakcji. Jeśli transakcja jest w toku, aktualizacja nie ostatecznie do czasu zatwierdzania transakcji. Dzięki temu można przejąć lub wycofać zmiany. Aby uzyskać informacje dotyczące transakcji, zobacz [transakcja (ODBC)](../../data/odbc/transaction-odbc.md).  
  
W poniższej tabeli przedstawiono opcje dostępne dla zestawów rekordów przy użyciu właściwości inną aktualizację.  
  
### <a name="recordset-readupdate-options"></a>Opcje Read/Update zestawu rekordów  
  
|Typ|Odczyt|Edytowanie rekordu|Usuwanie rekordu|Dodaj nowy (Dołącz)|  
|----------|----------|-----------------|-------------------|------------------------|  
|tylko do odczytu|T|N|N|N|  
|Tylko do dołączania|T|N|N|T|  
|W pełni nadaje się do aktualizacji|T|T|T|T|  
  
##  <a name="_core_determining_whether_your_recordset_is_updatable"></a> Określanie czy Twój zestaw rekordów jest Updateable  

Obiekt zestawu rekordów jest można aktualizować, jeśli źródło danych jest można aktualizować i otworzyć zestawu rekordów, co można aktualizować. Jego updateability zależy również od instrukcji SQL, można użyć możliwości sterownika ODBC i tego, czy Biblioteka kursorów ODBC znajduje się w pamięci. Nie można zaktualizować tylko do odczytu rekordów lub źródła danych.  
  
#### <a name="to-determine-whether-your-recordset-is-updatable"></a>Aby ustalić, czy rekordów nadaje się do  
  
1. Wywołanie obiektu zestawu rekordów [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) funkcja elementu członkowskiego.  
  
     `CanUpdate` Zwraca wartość różną od zera, jeśli zestaw rekordów jest można aktualizować.  
  
Domyślnie zestawy rekordów są w pełni można aktualizować (można wykonywać `AddNew`, `Edit`, i `Delete` operacji). Ale można również użyć [TylkoDołącz](../../mfc/reference/crecordset-class.md#open) opcję, aby otworzyć można aktualizować zestawy rekordów. Zestaw rekordów, otworzyć w ten sposób umożliwia dodawanie nowych rekordów z `AddNew`. Nie można edytować ani usunąć istniejące rekordy. Możesz sprawdzić, czy zestaw rekordów jest otwarty tylko w przypadku dołączania, wywołując [CanAppend](../../mfc/reference/crecordset-class.md#canappend) funkcja elementu członkowskiego. `CanAppend` Zwraca wartość różną od zera, jeśli zestaw rekordów jest w pełni można aktualizować lub otwarty tylko do dołączania.  
  
Poniższy kod pokazuje, jak można wykorzystać `CanUpdate` dla obiektu zestaw rekordów o nazwie `rsStudentSet`:  
  
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
>  Po przygotowaniu zaktualizuj zestaw rekordów, wywołując `Update`, zajmie się, że rekordów zawiera wszystkich kolumn tworzących klucza podstawowego tabeli (lub wszystkie kolumny wszelkie unikatowego indeksu dla tabeli). W niektórych przypadkach ramach służy tylko do kolumn, które zostały wybrane w twoim zestawie rekordów do zidentyfikować rekordy w tabeli, aby zaktualizować. Nie wszystkie niezbędne kolumny wielu rekordów mogły zostać zaktualizowane w tabeli, a w konsekwencji uszkodzenia integralności referencyjnej w tabeli. W tym przypadku ramach zgłasza wyjątki podczas wywoływania `Update`.  
  
##  <a name="_core_adding_a_record_to_a_recordset"></a> Dodawanie rekordu do zestawu rekordów  

Można dodać nowych rekordów do zestawu rekordów, jeśli jego [CanAppend](../../mfc/reference/crecordset-class.md#canappend) funkcja elementu członkowskiego zwraca wartość różną od zera.  
  
#### <a name="to-add-a-new-record-to-a-recordset"></a>Aby dodać nowy rekord do zestawu rekordów  
  
1. Upewnij się, że zestaw rekordów jest appendable.  
  
1. Wywołanie obiektu zestawu rekordów [działają funkcje AddNew](../../mfc/reference/crecordset-class.md#addnew) funkcja elementu członkowskiego.  
  
     `AddNew` przygotowuje rekordów pełnić rolę buforu edycji. Wszystkie elementy członkowskie danych pola są ustawiane na specjalna wartość Null i oznaczona jako niezmieniony, więc tylko zmienione (zakłóconych) wartości są zapisywane do źródła danych, gdy wywołujesz [aktualizacji](../../mfc/reference/crecordset-class.md#update).  
  
1. Ustaw wartości elementów członkowskich danych pola nowego rekordu.  
  
     Przypisz wartości do pól składowych danych. Te, które nie należy przypisywać nie są zapisywane do źródła danych.  
  
1. Wywołanie obiektu zestawu rekordów `Update` funkcja elementu członkowskiego.  
  
     `Update` Wykonuje dodawanie, pisząc nowy rekord w źródle danych. Dla informacji na temat się dzieje w przypadku awarii do wywołania `Update`, zobacz [zestaw rekordów: jak zestawy rekordów uaktualniają rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
Aby uzyskać informacje dotyczące sposobu dodawania rejestruje działania i kiedy dodano rekordy są widoczne w twoim zestawie rekordów, zobacz [zestaw rekordów: jak działają funkcje AddNew, Edit i Usuń pracy (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md).  
  
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
>  Aby anulować `AddNew` lub `Edit` wywołanie, po prostu wywoływania innej `AddNew` lub `Edit` lub zadzwoń `Move` z *AFX_MOVE_REFRESH* parametru. Elementy członkowskie danych zostaną przywrócone poprzednie wartości i są w dalszym ciągu w `Edit` lub `Add` trybu.  
  
##  <a name="_core_editing_a_record_in_a_recordset"></a> Edytowanie rekordu w zestawie rekordów  

Jeśli możesz edytować istniejące rekordy w zestawie rekordów [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) funkcja elementu członkowskiego zwraca wartość różną od zera.  
  
#### <a name="to-edit-an-existing-record-in-a-recordset"></a>Aby edytować istniejący rekord w zestawie rekordów  
  
1. Upewnij się, że zestaw rekordów jest można aktualizować.  
  
1. Przewiń do rekordu, który chcesz zaktualizować.  
  
1. Wywołanie obiektu zestawu rekordów [Edytuj](../../mfc/reference/crecordset-class.md#edit) funkcja elementu członkowskiego.  
  
     `Edit` przygotowuje rekordów pełnić rolę buforu edycji. Wszystkie elementy członkowskie danych pola są oznaczone i zestawu rekordów stwierdzić później, czy zostały zmienione. Nowe wartości dla elementów członkowskich danych zmienionego pola są zapisywane do źródła danych, gdy wywołujesz [aktualizacji](../../mfc/reference/crecordset-class.md#update).  
  
1. Ustaw wartości elementów członkowskich danych pola nowego rekordu.  
  
     Przypisz wartości do pól składowych danych. Te wartości nie należy przypisywać pozostaną bez zmian.  
  
1. Wywołanie obiektu zestawu rekordów `Update` funkcja elementu członkowskiego.  
  
     `Update` kończy edycji, pisząc zmienionego rekordu w źródle danych. Dla informacji na temat się dzieje w przypadku awarii do wywołania `Update`, zobacz [zestaw rekordów: jak zestawy rekordów uaktualniają rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
Po zakończeniu edycji rekordu, edytowany rekord pozostaje bieżącego rekordu.  
  
W poniższym przykładzie przedstawiono `Edit` operacji. Założono, że użytkownik został przeniesiony do rekordu, które użytkownik chce edytować.  
  
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
>  Aby anulować `AddNew` lub `Edit` wywołanie, po prostu wywoływania innej `AddNew` lub `Edit` lub zadzwoń `Move` z *AFX_MOVE_REFRESH* parametru. Elementy członkowskie danych zostaną przywrócone poprzednie wartości i są w dalszym ciągu w `Edit` lub `Add` trybu.  
  
##  <a name="_core_deleting_a_record_from_a_recordset"></a> Usuwanie rekordu z zestawu rekordów  

Rekordy można usunąć, jeśli w zestawie rekordów [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) funkcja elementu członkowskiego zwraca wartość różną od zera.  
  
#### <a name="to-delete-a-record"></a>Aby usunąć rekord  
  
1. Upewnij się, że zestaw rekordów jest można aktualizować.  
  
1. Przewiń do rekordu, który chcesz zaktualizować.  
  
1. Wywołanie obiektu zestawu rekordów [Usuń](../../mfc/reference/crecordset-class.md#delete) funkcja elementu członkowskiego.  
  
     `Delete` natychmiast oznacza rekord jako usunięty, zarówno w zestawie danych, jak i w źródle danych.  
  
     W odróżnieniu od `AddNew` i `Edit`, `Delete` nie ma odpowiedniego `Update` wywołania.  
  
1. Przewiń do innego rekordu.  
  
    > [!NOTE]
    >  Podczas przechodzenia przez zestaw rekordów, usuniętych rekordów nie mogły zostać pominięte. Aby uzyskać więcej informacji, zobacz [IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted) funkcja elementu członkowskiego.  
  
W poniższym przykładzie przedstawiono `Delete` operacji. Przyjęto założenie, że użytkownik została przeniesiona do rekordu, który użytkownik chce usunąć. Po `Delete` jest wywoływana, ważne jest, aby przejść do nowego rekordu.  
  
```  
rsStudent.Delete( );  
rsStudent.MoveNext( );  
```  
  
Aby uzyskać więcej informacji o skutkach `AddNew`, `Edit`, i `Delete` funkcji elementów członkowskich, zobacz [zestaw rekordów: jak zestawy rekordów uaktualniają rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
## <a name="see-also"></a>Zobacz też  

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: blokowanie rekordów (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)