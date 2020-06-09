---
title: Oczyszczanie dokumentów i widoków
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], cleaning up
- documents [MFC], cleaning up
- documents [MFC], closing
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
ms.openlocfilehash: 8cb6e9337b69daf78286f57898c9badf513c7921
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626526"
---
# <a name="cleaning-up-documents-and-views"></a>Oczyszczanie dokumentów i widoków

Gdy dokument zostanie zamknięty, struktura najpierw wywołuje jego funkcję członkowską [DeleteContents](reference/cdocument-class.md#deletecontents) . W przypadku przydzielenia dowolnej ilości pamięci na stercie w trakcie operacji dokumentu, `DeleteContents` najlepszym miejscem, aby ją cofnąć.

> [!NOTE]
> Nie należy cofać alokacji danych dokumentu w destruktorze dokumentu. W przypadku aplikacji SDI, obiekt dokumentu może być ponownie używany.

Można zastąpić destruktor widoku, aby cofnąć alokację dowolnej pamięci przydzieloną na stercie.

## <a name="see-also"></a>Zobacz też

[Inicjowanie i oczyszczanie dokumentów i widoków](initializing-and-cleaning-up-documents-and-views.md)
