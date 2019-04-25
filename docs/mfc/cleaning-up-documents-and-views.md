---
title: Oczyszczanie dokumentów i widoków
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], cleaning up
- documents [MFC], cleaning up
- documents [MFC], closing
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
ms.openlocfilehash: 940c768823d26950d9710fb1d1a52e6a1955fead
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62327161"
---
# <a name="cleaning-up-documents-and-views"></a>Oczyszczanie dokumentów i widoków

Gdy dokument zostanie zamknięty, struktura najpierw wywołuje jego [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) funkcja elementu członkowskiego. Jeśli została przydzielona w trakcie operacji na dokumencie, wszystkie pamięci na stosie `DeleteContents` jest najlepszym miejscem, aby cofnąć jej przydział.

> [!NOTE]
>  Nie należy cofnąć przydział danych dokumentu w destruktorze dokumentu. W przypadku aplikacji interfejsu SDI obiekt dokumentu może być ponownie używane.

Można zastąpić destruktor widoku można cofnąć alokacji wszelkie pamięci przydzielony na stosie.

## <a name="see-also"></a>Zobacz także

[Inicjowanie i oczyszczanie dokumentów i widoków](../mfc/initializing-and-cleaning-up-documents-and-views.md)
