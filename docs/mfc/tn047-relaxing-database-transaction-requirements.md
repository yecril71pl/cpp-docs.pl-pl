---
title: 'TN047: mniejsze wymagania dotyczące transakcji bazy danych'
ms.date: 11/04/2016
f1_keywords:
- vc.data
helpviewer_keywords:
- TN047
ms.assetid: f93c51cf-a8c0-43d0-aa47-7bcb8333d693
ms.openlocfilehash: d609576c5ffda1a3ba8021e6a459943092c40e98
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658838"
---
# <a name="tn047-relaxing-database-transaction-requirements"></a>TN047: mniejsze wymagania dotyczące transakcji bazy danych

Ta uwaga techniczna i omówiono wymagania dotyczące transakcji z klas baz danych MFC ODBC, jest teraz przestarzały. Przed MFC 4.2 klas baz danych wymagane zachowane kursory na zestawy rekordów po **CommitTrans** lub **wycofywania** operacji. Jeśli sterownik ODBC i DBMS obsługuje zachowania kursora na tym poziomie, następnie klas baz danych nie włączono w transakcji.

Począwszy od MFC 4.2, klas baz danych ma luźniejsze ograniczenie konieczności konserwowania kursora. Transakcje zostaną włączone, jeśli sterownik je obsługuje. Jednakże, teraz należy sprawdzić efekt skonfigurowania **CommitTrans** lub **wycofywania** operacji na otwarty zestaw rekordów. Zobacz funkcje elementów członkowskich [CDatabase::GetCursorCommitBehavior](../mfc/reference/cdatabase-class.md#getcursorcommitbehavior) i [CDatabase::GetCursorRollbackBehavior](../mfc/reference/cdatabase-class.md#getcursorrollbackbehavior) Aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

