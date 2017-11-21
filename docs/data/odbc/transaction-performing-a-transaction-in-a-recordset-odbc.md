---
title: "Transakcja: Wykonywanie transakcji w zestawie rekordów (ODBC) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: transactions, updating recordsets
ms.assetid: cf1d6b48-7fb8-4903-84f7-a1822054534d
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1451775374b94bbefb6396e7afeda2396df84ba4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="transaction-performing-a-transaction-in-a-recordset-odbc"></a>Transakcja: wykonywanie transakcji w zestawie rekordów (ODBC)
W tym temacie opisano sposób wykonania transakcji w zestawie rekordów.  
  
> [!NOTE]
>  Obsługiwany jest tylko jeden poziom transakcji; Nie można zagnieździć transakcji.  
  
#### <a name="to-perform-a-transaction-in-a-recordset"></a>Do wykonania transakcji w zestawie rekordów  
  
1.  Wywołanie `CDatabase` obiektu **BeginTrans** funkcję elementu członkowskiego.  
  
2.  Jeśli nie zaimplementowano zbiorcze pobieranie z wiersza, wywołaj **AddNew lub zaktualizowania**, **edycji lub zaktualizowania**, i **usunąć** co najmniej jeden obiekt zestaw rekordów o tej samej funkcji Członkowskich Baza danych dowolną liczbę razy. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: Dodawanie, aktualizowanie i usuwanie rekordów (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md). Jeśli zaimplementowano wiersza zbiorcze pobieranie, należy napisać funkcji do aktualizowania źródła danych.  
  
3.  Na koniec wywołania `CDatabase` obiektu **CommitTrans** funkcję elementu członkowskiego. Jeśli wystąpi błąd w jednym z aktualizacji lub zdecydować anulować zmiany, wywołanie jej **wycofywania** funkcję elementu członkowskiego.  
  
 W poniższym przykładzie użyto dwóch zestawów rekordów do usunięcia z bazy danych rejestracji służbowe, usuwanie student z wszystkie klasy, w których jest zarejestrowany student rejestracji studenta. Ponieważ **usunąć** wywołań w obu zestawach rekordów musi się zakończyć powodzeniem, wymagana jest transakcja. W przykładzie założono istnienie `m_dbStudentReg`, zmiennej elementu członkowskiego typu `CDatabase` podłączone do źródła danych i klasy rekordów `CEnrollmentSet` i `CStudentSet`. `strStudentID` Zmienna uwzględnia wartość uzyskane od użytkownika.  
  
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
>  Wywoływanie **BeginTrans** ponownie bez wywoływania elementu **CommitTrans** lub **wycofywania** jest błędem.  
  
## <a name="see-also"></a>Zobacz też  
 [Transakcja (ODBC)](../../data/odbc/transaction-odbc.md)   
 [Transakcja: Jak transakcje wpływają na aktualizacje (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)   
 [Cdatabase — klasa](../../mfc/reference/cdatabase-class.md)   
 [Crecordset — klasa](../../mfc/reference/crecordset-class.md)