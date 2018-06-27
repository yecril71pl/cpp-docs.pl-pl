---
title: 'TN068: Wykonywanie transakcji za pomocą sterownika Microsoft Access 7 ODBC | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.data.odbc
dev_langs:
- C++
helpviewer_keywords:
- TN068 [MFC]
- transactions [MFC], calling BeginTrans
- transactions [MFC], Microsoft Access
ms.assetid: d3f8f5d9-b118-4194-be36-a1aefb630c45
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 653e1cf29ff2b2e2338df7e8e3a1e74d73a7d6fe
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36950230"
---
# <a name="tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver"></a>TN068: wykonywanie transakcji za pomocą sterownika Microsoft Access 7 ODBC Driver
> [!NOTE]
>  Poniższe uwagi techniczne nie został zaktualizowany, ponieważ została ona uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub niepoprawne. Najnowsze informacje zalecane jest, możesz wyszukać temat odsetek w indeksie dokumentacji online.  
  
 Ta uwaga opisuje sposób wykonywania transakcji, korzystając z klasami baz danych MFC ODBC i sterownika Microsoft Access 7.0 ODBC uwzględnione w wersji pakietu sterowników pulpitu ODBC firmy Microsoft 3.0.  
  
## <a name="overview"></a>Omówienie  
 Jeśli aplikacja bazy danych wykonuje transakcji, należy zachować ostrożność wywołać `CDatabase::BeginTrans` i `CRecordset::Open` w odpowiedniej kolejności w aplikacji. Sterownik programu Microsoft Access 7.0 używa aparatu bazy danych programu Microsoft Jet i Jet wymaga się, że aplikacja nie rozpoczął transakcji na wszystkie bazy danych ma otwartego kursora. Dla klas baz danych MFC ODBC, otwórz kursora jest równa otwarty `CRecordset` obiektu.  
  
 Po otwarciu rekordów przed wywołaniem `BeginTrans`, mogą nie być widoczne wszystkie komunikaty o błędach. Jednak żadnych rekordów aktualizuje Twojej aplikacji sprawia, że stają się stałe po wywołaniu `CRecordset::Update`, i aktualizacje zostaną nie wycofane przez wywołanie metody `Rollback`. Aby uniknąć tego problemu, należy wywołać `BeginTrans` pierwszy, a następnie otwórz zestaw rekordów.  
  
 MFC sprawdza, czy funkcja sterownik zachowanie przekazywania i wycofywania kursora. Klasa `CDatabase` oferuje dwie funkcje elementu członkowskiego, `GetCursorCommitBehavior` i `GetCursorRollbackBehavior`, można ustalić skutek każdej transakcji sieci Otwórz `CRecordset` obiektu. Dla sterownika Microsoft Access 7.0 ODBC funkcje Członkowskie zwracają `SQL_CB_CLOSE` ponieważ sterownik dostępu nie obsługuje zachowania kursora. W związku z tym należy wywołać `CRecordset::Requery` następujące `CommitTrans` lub `Rollback` operacji.  
  
 Gdy trzeba wykonać wiele transakcji po kolei, nie można wywołać `Requery` po pierwszej transakcji i ponownie uruchomić następny. Należy zamknąć przed wywołaniem dalej do zestawu rekordów `BeginTrans` w celu spełnienia wymagań firmy Jet. Ta uwaga techniczna opisano dwie metody obsługi tej sytuacji:  
  
-   Zamykanie zestawu rekordów po każdym poleceniu `CommitTrans` lub `Rollback` operacji.  
  
-   Przy użyciu funkcji ODBC API `SQLFreeStmt`.  
  
## <a name="closing-the-recordset-after-each-committrans-or-rollback-operation"></a>Zamykanie zestawu rekordów po każdej operacji wycofania lub CommitTrans  
 Przed rozpoczęciem transakcji, upewnij się, że obiekt zestawu rekordów jest zamknięty. Po wywołaniu `BeginTrans`, wywołaj zestawu rekordów `Open` funkcję elementu członkowskiego. Zamknij zestaw rekordów, natychmiast po wywołaniu `CommitTrans` lub `Rollback`. Należy pamiętać, że wielokrotne otwieranie i zamykanie zestawu rekordów może zmniejszyć wydajność aplikacji.  
  
## <a name="using-sqlfreestmt"></a>Przy użyciu SQLFreeStmt  
 Możesz również użyć funkcji interfejsu API ODBC `SQLFreeStmt` jawnego zamknięcia kursor po zakończeniu transakcji. Aby uruchomić innej transakcji, należy wywołać `BeginTrans` następuje `CRecordset::Requery`. Podczas wywoływania metody `SQLFreeStmt`, należy określić w zestawie rekordów HSTMT jako pierwszego parametru oraz *SQL_CLOSE* jako drugiego parametru. Ta metoda jest szybsza niż zamknięcie i otwarcie zestawu rekordów na początku każdej transakcji. Poniższy kod przedstawia sposób wykonania tej techniki:  
  
```  
CMyDatabase db;  
db.Open("MYDATASOURCE");

CMyRecordset rs(&db);

 
// start transaction 1 and   
// open the recordset  
db.BeginTrans();

rs.Open();

 
// manipulate data  
 
// end transaction 1  
db.CommitTrans();
*// or Rollback()  
 
// close the cursor  
::SQLFreeStmt(rs.m_hstmt, SQL_CLOSE);

 
// start transaction 2  
db.BeginTrans();

 
// now get the result set  
rs.Requery();

 
// manipulate data  
 
// end transaction 2  
db.CommitTrans();

 
rs.Close();

db.Close();
```  
  
 Innym sposobem wykonania ta technika jest napisanie nową funkcję, `RequeryWithBeginTrans`, który można wywołać w celu uruchomienia następnej transakcji po zatwierdzeniu lub wycofywania pierwszego. Aby napisać takich funkcji, wykonaj następujące czynności:  
  
1.  Skopiuj kod `CRecordset::Requery( )` nowych funkcji.  
  
2.  Dodaj następujący wiersz bezpośrednio po wywołaniu `SQLFreeStmt`:  
  
 `m_pDatabase->BeginTrans( );`  
  
 Teraz można wywołać tej funkcji, każda para transakcji:  
  
```  
// start transaction 1 and   
// open the recordset  
db.BeginTrans();

rs.Open();

 
// manipulate data  
 
// end transaction 1  
db.CommitTrans();
*// or Rollback()  
 
// close the cursor,
    start new transaction,  
// and get the result set  
rs.RequeryWithBeginTrans();

 
// manipulate data  
 
// end transaction 2  
db.CommitTrans();
*// or Rollback()  
```  
  
> [!NOTE]
>  Nie należy używać tej metody, jeśli musisz zmienić zmienne Członkowskie rekordów *m_strFilter* lub *m_strSort* między transakcji. W takim przypadku należy zamknąć zestawu rekordów po każdym poleceniu `CommitTrans` lub `Rollback` operacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

