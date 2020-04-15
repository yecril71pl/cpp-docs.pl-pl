---
title: Oczyszczanie dokumentów i widoków
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], cleaning up
- documents [MFC], cleaning up
- documents [MFC], closing
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
ms.openlocfilehash: 06ff60a2cf6245f64e80d899c13a8444558fcf0b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374619"
---
# <a name="cleaning-up-documents-and-views"></a>Oczyszczanie dokumentów i widoków

Po zamknięciu dokumentu, ramach najpierw wywołuje jego [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) funkcji elementu członkowskiego. Jeśli przydzielono dowolną pamięć na stercie w trakcie operacji `DeleteContents` dokumentu, jest najlepszym miejscem do deallocate go.

> [!NOTE]
> Nie należy rozdzielać danych dokumentu w destruktorze dokumentu. W przypadku aplikacji SDI obiekt dokumentu może być ponownie ponownie.

Można zastąpić destruktora widoku, aby zdeterminować dowolną pamięć przydzieloną na stercie.

## <a name="see-also"></a>Zobacz też

[Inicjowanie i oczyszczanie dokumentów i widoków](../mfc/initializing-and-cleaning-up-documents-and-views.md)
