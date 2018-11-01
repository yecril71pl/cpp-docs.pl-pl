---
title: 'Transakcja: wykonywanie transakcji w zestawie rekordów (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- transactions, updating recordsets
ms.assetid: cf1d6b48-7fb8-4903-84f7-a1822054534d
ms.openlocfilehash: df7c28ebfbb68f3e0163368247b90ff69058726d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50659598"
---
# <a name="transaction-performing-a-transaction-in-a-recordset-odbc"></a>Transakcja: wykonywanie transakcji w zestawie rekordów (ODBC)

W tym temacie opisano sposób wykonania transakcji w zestawie rekordów.

> [!NOTE]
>  Obsługiwana jest tylko jeden poziom transakcji; Nie można zagnieździć transakcji.

#### <a name="to-perform-a-transaction-in-a-recordset"></a>Do wykonania transakcji w zestawie rekordów

1. Wywołaj `CDatabase` obiektu `BeginTrans` funkcja elementu członkowskiego.

1. Jeśli nie zaimplementowano zbiorcze pobieranie z wiersza, należy wywołać `AddNew/Update`, `Edit/Update`, i `Delete` funkcji elementów członkowskich co najmniej jeden obiektów zestaw rekordów o tej samej bazy danych na dowolną liczbę razy. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: Dodawanie, aktualizowanie i usuwanie rekordów (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md). Jeśli zaimplementowano wiersz zbiorcze pobieranie, należy napisać własne funkcje, aby zaktualizować źródło danych.

1. Na koniec Wywołaj `CDatabase` obiektu `CommitTrans` funkcja elementu członkowskiego. Jeśli wystąpi błąd w jednej z aktualizacji lub zdecydować anulować zmiany, należy wywołać jej `Rollback` funkcja elementu członkowskiego.

W poniższym przykładzie użyto dwa zestawy rekordów do usunięcia rejestracji studenta z rejestracji bazy danych school, usuwając dla uczniów z wszystkie klasy, w których jest zarejestrowany dla uczniów. Ponieważ `Delete` wywołuje w obu zestawach rekordów musi zakończyć się sukcesem, wymagana jest transakcja. Przykład zakłada się istnienie `m_dbStudentReg`, zmienną składową typu `CDatabase` podłączony do źródła danych i klas zestawu rekordów `CEnrollmentSet` i `CStudentSet`. `strStudentID` Zmienna zawiera wartość uzyskanych od użytkownika.

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
>  Wywoływanie `BeginTrans` ponownie bez wywoływania `CommitTrans` lub `Rollback` , występuje błąd.

## <a name="see-also"></a>Zobacz też

[Transakcja (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[Transakcja: jak transakcje wpływają na aktualizacje (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)<br/>
[Klasa CDatabase](../../mfc/reference/cdatabase-class.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)