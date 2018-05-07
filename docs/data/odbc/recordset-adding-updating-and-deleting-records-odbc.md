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
ms.openlocfilehash: af3a3eb08ce5749c0cfe5ca2d1f59213826ff7ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="recordset-adding-updating-and-deleting-records-odbc"></a>Zestaw rekordów: dodawanie, aktualizowanie i usuwanie rekordów (ODBC)
Ten temat dotyczy klasach MFC ODBC.  
  
> [!NOTE]
>  Rekordy można teraz dodawać zbiorczo bardziej efektywnie. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: dodawanie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-adding-records-in-bulk-odbc.md).  
  
> [!NOTE]
>  Ten temat dotyczy obiektów pochodzących od `CRecordset` w wiersz, który zbiorczego pobierania nie została zaimplementowana. Jeśli korzystasz z zbiorcze pobieranie z wiersza, zobacz [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Można aktualizować migawki i zestawów dynamicznych umożliwiają dodawanie, edytowanie (aktualizacji) i usuwania rekordów. W tym temacie opisano:  
  
-   [Jak ustalić, czy zestawu rekordów nadaje się do](#_core_determining_whether_your_recordset_is_updatable).  
  
-   [Jak dodać nowy rekord](#_core_adding_a_record_to_a_recordset).  
  
-   [Edytowanie istniejącego rekordu](#_core_editing_a_record_in_a_recordset).  
  
-   [Jak usunąć rekord](#_core_deleting_a_record_from_a_recordset).  
  
 Aby uzyskać więcej informacji na temat sposobu aktualizacji są wykonywane się, a aktualizacje są wyświetlane dla innych użytkowników, zobacz [zestaw rekordów: jak zestawy rekordów aktualizacji rekordów (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md). Zwykle po dodać, edytować lub usunąć rekord zestawu rekordów zmienia natychmiast źródła danych. Można zamiast tego partii grup odpowiednich aktualizacji w transakcji. Jeśli transakcja jest w toku, aktualizacja nie ostatecznie do momentu zatwierdzić transakcji. Dzięki temu można przejąć ani wycofać zmian. Informacje o transakcjach, zobacz [transakcja (ODBC)](../../data/odbc/transaction-odbc.md).  
  
 W poniższej tabeli przedstawiono opcje dostępne dla zestawów rekordów o charakterystyce innej aktualizacji.  
  
### <a name="recordset-readupdate-options"></a>Opcje Read/Update zestawu rekordów  
  
|Typ|Odczyt|Edycja rekordów|Usuwanie rekordu|Dodaj nowy (Dołącz)|  
|----------|----------|-----------------|-------------------|------------------------|  
|tylko do odczytu|T|N|N|N|  
|Tylko Dołącz|T|N|N|T|  
|Pełni nadaje się do aktualizacji|T|T|T|T|  
  
##  <a name="_core_determining_whether_your_recordset_is_updatable"></a> Określanie rekordów Your czy to Updateable  
 Obiekty zestawów rekordów jest można aktualizować, jeśli źródło danych jest można aktualizować i otworzyć zestawu rekordów, jak można aktualizować. Czy można ją aktualizować zależy również od instrukcji SQL, można użyć funkcji sterownika ODBC i określa, czy Biblioteka kursorów ODBC znajduje się w pamięci. Nie można zaktualizować tylko do odczytu źródła danych lub zestawu rekordów.  
  
#### <a name="to-determine-whether-your-recordset-is-updatable"></a>Aby określić, czy nadaje zestawu rekordów  
  
1.  Wywołanie obiektu zestawu rekordów [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) funkcję elementu członkowskiego.  
  
     `CanUpdate` Zwraca wartość niezerową, jeśli można aktualizować zestawu rekordów.  
  
 Zestawy rekordów są domyślnie pełni aktualizowalne (można wykonywać `AddNew`, **Edytuj**, i **usunąć** operacji). Można używać również [TylkoDołącz](../../mfc/reference/crecordset-class.md#open) opcję, aby otworzyć można aktualizować zestawów rekordów. Zestaw rekordów otworzyć w ten sposób umożliwia dodawanie nowych rekordów z `AddNew`. Nie można edytować lub usunąć istniejące rekordy. Można sprawdzić, czy zestaw rekordów jest otwarty tylko w przypadku dołączania wywołując [CanAppend](../../mfc/reference/crecordset-class.md#canappend) funkcję elementu członkowskiego. `CanAppend` Zwraca wartość niezerową, jeśli zestaw rekordów jest całkowicie można aktualizować lub Otwórz tylko do dołączenia.  
  
 Poniższy kod przedstawia, jak można użyć `CanUpdate` dla obiekt zestaw rekordów o nazwie `rsStudentSet`:  
  
```  
if( !rsStudentSet.Open( ) )  
    return FALSE;  
if( !rsStudentSet.CanUpdate( ) )  
{  
    AfxMessageBox( "Unable to update the Student recordset." );  
    return;  
}  
```  
  
> [!CAUTION]
>  Podczas przygotowania do aktualizacji zestawu rekordów przez wywołanie metody **aktualizacji**, zwrócić uwagę, że zestawu rekordów zawiera wszystkie kolumny tworzące klucz podstawowy tabeli (lub wszystkie kolumny żadnych unikatowy indeks w tej tabeli). W niektórych przypadkach framework może być zidentyfikować rekordy w tabeli, aby zaktualizować tylko kolumny wybrana w twoim zestawie rekordów. Nie wszystkie kolumny niezbędne wiele rekordów mogły zostać zaktualizowane w tabeli, prawdopodobnie uszkodzenia integralności referencyjnej w tabeli. W takim przypadku platformę zgłasza wyjątki podczas wywoływania **aktualizacji**.  
  
##  <a name="_core_adding_a_record_to_a_recordset"></a> Dodawanie rekordu do zestawu rekordów  
 Można dodać nowych rekordów do zestawu rekordów, jeśli jego [CanAppend](../../mfc/reference/crecordset-class.md#canappend) — członek, funkcja zwraca wartość różną od zera.  
  
#### <a name="to-add-a-new-record-to-a-recordset"></a>Aby dodać nowego rekordu do zestawu rekordów  
  
1.  Upewnij się, że zestaw rekordów jest appendable.  
  
2.  Wywołanie obiektu zestawu rekordów [AddNew](../../mfc/reference/crecordset-class.md#addnew) funkcję elementu członkowskiego.  
  
     `AddNew` przygotowuje rekordów do działania jako bufor edycji. Wszystkie elementy członkowskie danych pola są specjalne wartość Null, jest oznaczona jako bez zmian, tylko zmienione (brudne) wartości są zapisywane do źródła danych podczas wywoływania [aktualizacji](../../mfc/reference/crecordset-class.md#update).  
  
3.  Ustaw wartości elementy członkowskie danych pola w nowym rekordzie.  
  
     Przypisanie wartości do elementy członkowskie danych pola. Te, które nie należy przypisywać nie są zapisywane w źródle danych.  
  
4.  Wywołanie obiektu zestawu rekordów **aktualizacji** funkcję elementu członkowskiego.  
  
     **Aktualizacja** wykonuje dodanie przez Zapisywanie nowego rekordu w źródle danych. Dla informacji o się stanie, jeśli nie zostanie wywołać **aktualizacji**, zobacz [zestaw rekordów: jak zestawy rekordów aktualizacji rekordów (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
 Aby uzyskać informacje dotyczące sposobu dodawania rejestruje działania i kiedy dodano rekordy są widoczne w zestawu rekordów, zobacz [zestaw rekordów: jak AddNew, Edit i usunąć pracy (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md).  
  
 Poniższy przykład przedstawia sposób dodawania nowego rekordu:  
  
```  
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
>  Aby anulować `AddNew` lub **Edytuj** wywołać, po prostu wywoływania innego `AddNew` lub **Edytuj** lub zadzwoń **Przenieś** z **AFX_MOVE_REFRESH**  parametru. Elementy członkowskie danych zostaną przywrócone poprzednie wartości i są w dalszym ciągu w **Edytuj** lub **Dodaj** tryb.  
  
##  <a name="_core_editing_a_record_in_a_recordset"></a> Edytowanie rekordu w zestawie rekordów  
 Można edytować istniejące rekordy w zestawie rekordów [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) — członek, funkcja zwraca wartość różną od zera.  
  
#### <a name="to-edit-an-existing-record-in-a-recordset"></a>Aby edytować istniejący rekord w zestawie rekordów  
  
1.  Upewnij się, że zestaw rekordów jest można aktualizować.  
  
2.  Przewiń do rekordu, który chcesz zaktualizować.  
  
3.  Wywołanie obiektu zestawu rekordów [Edytuj](../../mfc/reference/crecordset-class.md#edit) funkcję elementu członkowskiego.  
  
     **Edytuj** przygotowuje rekordów do działania jako bufor edycji. Wszystkie elementy członkowskie danych pola są oznaczone tak, aby zestaw rekordów stwierdzić później, czy zostały zmienione. Nowe wartości dla pola zmienione elementy członkowskie danych są zapisywane do źródła danych podczas wywoływania [aktualizacji](../../mfc/reference/crecordset-class.md#update).  
  
4.  Ustaw wartości elementy członkowskie danych pola w nowym rekordzie.  
  
     Przypisanie wartości do elementy członkowskie danych pola. Te wartości nie należy przypisywać pozostają niezmienione.  
  
5.  Wywołanie obiektu zestawu rekordów **aktualizacji** funkcję elementu członkowskiego.  
  
     **Aktualizacja** zakończeniu edycji przez zapisywanie zmienionych rekordów w źródle danych. Dla informacji o się stanie, jeśli nie zostanie wywołać **aktualizacji**, zobacz [zestaw rekordów: jak zestawy rekordów aktualizacji rekordów (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
 Po przeprowadzeniu edycji rekordu, edytowanego rekordu pozostaje bieżącego rekordu.  
  
 W poniższym przykładzie przedstawiono **Edytuj** operacji. Zakłada się, że użytkownik został przeniesiony do rekordu, które użytkownik chce edytować.  
  
```  
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
>  Aby anulować `AddNew` lub **Edytuj** wywołać, po prostu wywoływania innego `AddNew` lub **Edytuj** lub zadzwoń **Przenieś** z **AFX_MOVE_REFRESH**  parametru. Elementy członkowskie danych zostaną przywrócone poprzednie wartości i są w dalszym ciągu w **Edytuj** lub **Dodaj** tryb.  
  
##  <a name="_core_deleting_a_record_from_a_recordset"></a> Usunięcie rekordu z zestawu rekordów  
 Rekordy można usunąć, jeśli w zestawie rekordów [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) — członek, funkcja zwraca wartość różną od zera.  
  
#### <a name="to-delete-a-record"></a>Aby usunąć rekord  
  
1.  Upewnij się, że zestaw rekordów jest można aktualizować.  
  
2.  Przewiń do rekordu, który chcesz zaktualizować.  
  
3.  Wywołanie obiektu zestawu rekordów [usunąć](../../mfc/reference/crecordset-class.md#delete) funkcję elementu członkowskiego.  
  
     **Usuń** natychmiast oznacza rekord jako usunięte, zarówno w zestawie rekordów, jak i w źródle danych.  
  
     W odróżnieniu od `AddNew` i **Edytuj**, **usunąć** nie ma odpowiedniego **aktualizacji** wywołania.  
  
4.  Przewiń do innego rekordu.  
  
    > [!NOTE]
    >  Podczas przenoszenia za pomocą zestawu rekordów, usuniętych rekordów nie mogły zostać pominięte. Aby uzyskać więcej informacji, zobacz [IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted) funkcję elementu członkowskiego.  
  
 W poniższym przykładzie przedstawiono **usunąć** operacji. Przyjęto założenie, że użytkownik został przeniesiony rekordu, który chcesz usunąć. Po **usunąć** jest wywoływana, ważne jest, aby przenieść do nowego rekordu.  
  
```  
rsStudent.Delete( );  
rsStudent.MoveNext( );  
```  
  
 Aby uzyskać więcej informacji o skutkach `AddNew`, **Edytuj**, i **usunąć** funkcji członkowskiej, zobacz [zestaw rekordów: jak zestawy rekordów aktualizacji rekordów (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Zestaw rekordów: blokowanie rekordów (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)