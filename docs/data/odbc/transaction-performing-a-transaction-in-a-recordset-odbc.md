---
title: 'Transakcja: wykonywanie transakcji w zestawie rekordów (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- transactions, updating recordsets
ms.assetid: cf1d6b48-7fb8-4903-84f7-a1822054534d
ms.openlocfilehash: 45ae414c318376b2c4d787498e9a288a0037af83
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358093"
---
# <a name="transaction-performing-a-transaction-in-a-recordset-odbc"></a>Transakcja: wykonywanie transakcji w zestawie rekordów (ODBC)

W tym temacie wyjaśniono, jak wykonać transakcję w zamówiórie.

> [!NOTE]
> Obsługiwany jest tylko jeden poziom transakcji; nie można zagnieżdżać transakcji.

#### <a name="to-perform-a-transaction-in-a-recordset"></a>Aby wykonać transakcję w ach recordset

1. Wywołanie `CDatabase` funkcji `BeginTrans` elementu członkowskiego obiektu.

1. Jeśli pobieranie wiersza zbiorczego nie zostało `AddNew/Update`zaimplementowane, należy wywołać funkcje , `Edit/Update`i `Delete` element członkowski jednego lub więcej obiektów ciekawego z tej samej bazy danych tyle razy, ile potrzeba. Aby uzyskać więcej informacji, zobacz [Tablica rekordów: Dodawanie, aktualizowanie i usuwanie rekordów (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md). Jeśli zaimplementowano pobieranie wiersza zbiorczego, należy napisać własne funkcje, aby zaktualizować źródło danych.

1. Na koniec wywołać `CDatabase` funkcję `CommitTrans` elementu członkowskiego obiektu. Jeśli wystąpi błąd w jednej z aktualizacji lub zdecydujesz się `Rollback` anulować zmiany, wywołaj jego funkcję członkową.

W poniższym przykładzie użyto dwóch rekordów, aby usunąć rejestrację ucznia z szkolnej bazy danych rejestracji, usuwając ucznia ze wszystkich klas, w których uczeń jest zapisany. Ponieważ `Delete` wywołania w obu zestawy rekordów musi zakończyć się pomyślnie, transakcja jest wymagana. W przykładzie przyjęto `m_dbStudentReg`założenie istnienia , `CDatabase` zmiennej członkowskiej typu już połączone `CEnrollmentSet` `CStudentSet`ze źródłem danych i recordset klasy i . Zmienna `strStudentID` zawiera wartość uzyskaną od użytkownika.

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
> Wywołanie `BeginTrans` ponownie `CommitTrans` `Rollback` bez wywoływania lub jest błędem.

## <a name="see-also"></a>Zobacz też

[Transakcja (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[Transakcja: jak transakcje wpływają na aktualizacje (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)<br/>
[Klasa CDatabase](../../mfc/reference/cdatabase-class.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)
