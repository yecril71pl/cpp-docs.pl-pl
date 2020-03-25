---
title: 'Transakcja: wykonywanie transakcji w zestawie rekordów (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- transactions, updating recordsets
ms.assetid: cf1d6b48-7fb8-4903-84f7-a1822054534d
ms.openlocfilehash: 94177a27a1f99a8c9c37b7fce3f697fd0088b7c6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212592"
---
# <a name="transaction-performing-a-transaction-in-a-recordset-odbc"></a>Transakcja: wykonywanie transakcji w zestawie rekordów (ODBC)

W tym temacie wyjaśniono, jak wykonać transakcję w zestawie rekordów.

> [!NOTE]
>  Obsługiwany jest tylko jeden poziom transakcji; nie można zagnieżdżać transakcji.

#### <a name="to-perform-a-transaction-in-a-recordset"></a>Aby wykonać transakcję w zestawie rekordów

1. Wywołaj `BeginTrans`ą funkcję członkowską obiektu `CDatabase`.

1. Jeśli nie zaimplementowano pobierania wierszy zbiorczych, wywołaj funkcje składowe `AddNew/Update`, `Edit/Update`i `Delete` z co najmniej jednego obiektu zestawu rekordów w tej samej bazie danych tyle razy, ile jest to konieczne. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: Dodawanie, aktualizowanie i usuwanie rekordów (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md). Jeśli zaimplementowano pobieranie wierszy zbiorczych, należy napisać własne funkcje, aby zaktualizować źródło danych.

1. Na koniec wywołaj funkcję członkowską `CommitTrans` obiektu `CDatabase`. Jeśli w jednej z aktualizacji wystąpi błąd lub zdecydujesz się anulować zmiany, wywołaj jego `Rollback` funkcję członkowską.

W poniższym przykładzie zastosowano dwa zestawy rekordów, aby usunąć rejestrację ucznia z bazy danych rejestracji szkoły, usuwając uczniów ze wszystkich klas, w których student jest zarejestrowany. Ponieważ wywołania `Delete` w obu zestawach rekordów muszą się zakończyć pomyślnie, wymagana jest transakcja. W przykładzie przyjęto założenie, że istnieje `m_dbStudentReg`, zmienna członkowska typu `CDatabase` już połączona ze źródłem danych, a klasy zestawu rekordów `CEnrollmentSet` i `CStudentSet`. Zmienna `strStudentID` zawiera wartość uzyskaną od użytkownika.

```
BOOL CEnrollDoc::RemoveStudent( CString strStudentID )
{
    // remove student from all the classes
    // the student is enrolled in

    if ( !m_dbStudentReg.BeginTrans( ) )
        return FALSE;

    CEnrollmentSet rsEnrollmentSet(&m_dbStudentReg);
    rsEnrollmentSet.m_strFilter = "StudentID = " + strStudentID;

    if ( !rsEnrollmentSet.Open(CRecordset::dynaset) )
        return FALSE;

    CStudentSet rsStudentSet(&m_dbStudentReg);
    rsStudentSet.m_strFilter = "StudentID = " + strStudentID;

    if ( !rsStudentSet.Open(CRecordset::dynaset) )
        return FALSE;

    TRY
    {
        while ( !rsEnrollmentSet.IsEOF( ) )
        {
            rsEnrollmentSet.Delete( );
            rsEnrollmentSet.MoveNext( );
        }

        // delete the student record
        rsStudentSet.Delete( );

        m_dbStudentReg.CommitTrans( );
    }

    CATCH_ALL(e)
    {
        m_dbStudentReg.Rollback( );
        return FALSE;
    }
    END_CATCH_ALL

    rsEnrollmentSet.Close( );
    rsStudentSet.Close( );

    return TRUE;

}
```

> [!NOTE]
>  Wywołanie `BeginTrans` ponownie bez wywoływania `CommitTrans` lub `Rollback` jest błędem.

## <a name="see-also"></a>Zobacz też

[Transakcja (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[Transakcja: jak transakcje wpływają na aktualizacje (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)<br/>
[Klasa CDatabase](../../mfc/reference/cdatabase-class.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)
