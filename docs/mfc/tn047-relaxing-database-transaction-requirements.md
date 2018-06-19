---
title: 'TN047: Mniejsze wymagania dotyczące transakcji bazy danych | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: be5870efacb61d5c0bb74f85427c41f787d2edd6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33380937"
---
# <a name="tn047-relaxing-database-transaction-requirements"></a>TN047: mniejsze wymagania dotyczące transakcji bazy danych
Ta uwaga techniczna, omówiono wymagania dotyczące transakcji z klasami baz danych MFC ODBC, jest już nieaktualny. Przed MFC 4.2 klasy baz danych wymagane zachowywanie kursorów na zestawy rekordów po **CommitTrans** lub **wycofywania** operacji. Jeśli sterownik ODBC i bazami danych nie obsługuje tego poziomu zachowywania kursora, klas baz danych nie włączono transakcji.  
  
 Począwszy od MFC 4.2, klas baz danych ma rozluźnić ograniczenia konieczności zachowania kursora. Transakcje zostanie włączona, jeśli sterownik je obsługuje. Jednak musisz teraz sprawdzić efekt **CommitTrans** lub **wycofywania** operacji na otwieranie zestawów rekordów. Zobacz funkcje Członkowskie [CDatabase::GetCursorCommitBehavior](../mfc/reference/cdatabase-class.md#getcursorcommitbehavior) i [CDatabase::GetCursorRollbackBehavior](../mfc/reference/cdatabase-class.md#getcursorrollbackbehavior) Aby uzyskać więcej informacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

