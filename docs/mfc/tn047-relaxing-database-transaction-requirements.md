---
title: ': Tn047 mniejsze wymagania dotyczące transakcji bazy danych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.data
dev_langs:
- C++
helpviewer_keywords:
- TN047
ms.assetid: f93c51cf-a8c0-43d0-aa47-7bcb8333d693
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 96f3116f503ffa0ffc461ea2c1a0bdaf8947a0be
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427020"
---
# <a name="tn047-relaxing-database-transaction-requirements"></a>TN047: mniejsze wymagania dotyczące transakcji bazy danych

Ta uwaga techniczna i omówiono wymagania dotyczące transakcji z klas baz danych MFC ODBC, jest teraz przestarzały. Przed MFC 4.2 klas baz danych wymagane zachowane kursory na zestawy rekordów po **CommitTrans** lub **wycofywania** operacji. Jeśli sterownik ODBC i DBMS obsługuje zachowania kursora na tym poziomie, następnie klas baz danych nie włączono w transakcji.

Począwszy od MFC 4.2, klas baz danych ma luźniejsze ograniczenie konieczności konserwowania kursora. Transakcje zostaną włączone, jeśli sterownik je obsługuje. Jednakże, teraz należy sprawdzić efekt skonfigurowania **CommitTrans** lub **wycofywania** operacji na otwarty zestaw rekordów. Zobacz funkcje elementów członkowskich [CDatabase::GetCursorCommitBehavior](../mfc/reference/cdatabase-class.md#getcursorcommitbehavior) i [CDatabase::GetCursorRollbackBehavior](../mfc/reference/cdatabase-class.md#getcursorrollbackbehavior) Aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

