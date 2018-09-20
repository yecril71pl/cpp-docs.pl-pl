---
title: 'TN068: Wykonywanie transakcji za pomocą sterownika Microsoft Access 7 ODBC | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 06/28/2018
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
ms.openlocfilehash: 4006ee6953342fd55b644eeb2a8e8f30c1d80285
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395846"
---
# <a name="tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver"></a>TN068: wykonywanie transakcji za pomocą sterownika Microsoft Access 7 ODBC Driver

> [!NOTE]
> Następująca uwaga techniczna nie został zaktualizowany od pierwszego uwzględnienia jej w dokumentacji online. W rezultacie niektóre procedury i tematy może być nieaktualne lub niepoprawne. Najnowsze informacje zaleca się wyszukać temat w indeksie dokumentacji online.

Ta uwaga opisuje sposób wykonywania transakcji, podczas korzystania z klas baz danych MFC ODBC i sterowników ODBC 7.0 dostępu firmy Microsoft objęte pakiet sterownika Desktop ODBC firmy Microsoft w wersji 3.0.

## <a name="overview"></a>Omówienie

Jeśli transakcje są wykonywane w aplikacji bazy danych, należy zachować ostrożność wywołać `CDatabase::BeginTrans` i `CRecordset::Open` w odpowiedniej kolejności, w aplikacji. Sterownik programu Microsoft Access 7.0 używa aparatu bazy danych Microsoft Jet i Jet wymaga, że aplikacja rozpocznie się transakcji w dowolnej bazy danych, który ma otwartego kursora. Dla klas baz danych MFC ODBC, otwartego kursora jest równa otwartą `CRecordset` obiektu.

Jeśli otworzysz zestaw rekordów przed wywołaniem `BeginTrans`, mogą nie być wyświetlane komunikaty o błędach. Jednak żadnych rekordów aktualizuje swoje sprawia, że aplikacja powoduje trwałe po wywołaniu `CRecordset::Update`, i aktualizacje zostaną nie można wycofać przez wywołanie metody `Rollback`. Aby uniknąć tego problemu, należy wywołać `BeginTrans` pierwszy, a następnie otwórz zestaw rekordów.

MFC sprawdza, czy funkcje sterownika zachowanie zatwierdzenia i wycofanie kursora. Klasa `CDatabase` zapewnia dwie funkcje Członkowskie, `GetCursorCommitBehavior` i `GetCursorRollbackBehavior`, aby ustalić skutki każdej transakcji dla usługi open `CRecordset` obiektu. Dla sterownika Microsoft Access 7.0 ODBC, te funkcje Członkowskie zwracają `SQL_CB_CLOSE` ponieważ sterownik dostępu nie obsługuje zachowania kursora. W związku z tym, należy wywołać `CRecordset::Requery` następujące `CommitTrans` lub `Rollback` operacji.

Gdy trzeba wykonać wiele transakcji, jedna po drugiej, nie można wywołać `Requery` po pierwszej transakcji i ponownie uruchomić kolejny. Należy zamknąć rekordów przed następnym wywołaniu `BeginTrans` w celu spełnienia wymagań firmy Jet. Ta uwaga techniczna opisano dwie metody obsługi tej sytuacji:

- Zamykanie zestawu rekordów po każdym poleceniu `CommitTrans` lub `Rollback` operacji.

- Za pomocą funkcji interfejsu API ODBC `SQLFreeStmt`.

## <a name="closing-the-recordset-after-each-committrans-or-rollback-operation"></a>Zamykanie zestawu rekordów po każdej z CommitTrans — lub operacji wycofywania

Przed rozpoczęciem transakcji, upewnij się, że obiekt zestawu rekordów jest zamknięty. Po wywołaniu `BeginTrans`, wywoływanie w zestawie rekordów `Open` funkcja elementu członkowskiego. Zamknij zestaw rekordów, natychmiast po wywołaniu `CommitTrans` lub `Rollback`. Należy pamiętać, że wielokrotnym otwieraniem i zamykaniem zestawu rekordów może spowolnić działanie aplikacji.

## <a name="using-sqlfreestmt"></a>Za pomocą SQLFreeStmt

Można również użyć funkcji interfejsu API ODBC `SQLFreeStmt` jawnego zamknięcia kursor po transakcji. Aby rozpocząć innej transakcji, należy wywołać `BeginTrans` następuje `CRecordset::Requery`. Podczas wywoływania `SQLFreeStmt`, należy określić w zestawie rekordów HSTMT jako pierwszego parametru i *SQL_CLOSE* jako drugi parametr. Ta metoda jest szybsza niż zamknąć i otworzyć zestawu rekordów na początku każdej transakcji. Poniższy kod demonstruje sposób implementacji tej techniki:

```cpp
CMyDatabase db;
db.Open("MYDATASOURCE");
CMyRecordset rs(&db);

// start transaction 1 and
// open the recordset
db.BeginTrans();
rs.Open();

// manipulate data

// end transaction 1
db.CommitTrans(); // or Rollback()

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

Innym sposobem realizowania tej techniki jest napisanie nową funkcję `RequeryWithBeginTrans`, które można wywołać, aby uruchomić dalej transakcji po zatwierdzeniu lub wycofania pierwszy z nich. Aby zapisać takich funkcji, wykonaj następujące czynności:

1. Skopiuj kod `CRecordset::Requery( )` na nową funkcję.

2. Dodaj następujący wiersz natychmiast po wywołaniu `SQLFreeStmt`:

   `m_pDatabase->BeginTrans( );`

Teraz można wywołać tę funkcję, każda para transakcji:

```cpp
// start transaction 1 and
// open the recordset
db.BeginTrans();

rs.Open();

// manipulate data

// end transaction 1
db.CommitTrans();   // or Rollback()

// close the cursor, start new transaction,
// and get the result set
rs.RequeryWithBeginTrans();

// manipulate data

// end transaction 2
db.CommitTrans();   // or Rollback()
```

> [!NOTE]
> Nie należy używać tej techniki, jeśli zajdzie potrzeba zmiany zmiennych składowych zestawu rekordów *m_strFilter* lub *m_strSort* między transakcji. W takim przypadku należy zamykać zestawu rekordów po każdym poleceniu `CommitTrans` lub `Rollback` operacji.

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
