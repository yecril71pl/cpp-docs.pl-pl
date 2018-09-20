---
title: Oczyszczanie dokumentów i widoków | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- views [MFC], cleaning up
- documents [MFC], cleaning up
- documents [MFC], closing
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f4325b0de10861fc76ee9ab816376f40ba0ba587
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46437420"
---
# <a name="cleaning-up-documents-and-views"></a>Oczyszczanie dokumentów i widoków

Gdy dokument zostanie zamknięty, struktura najpierw wywołuje jego [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) funkcja elementu członkowskiego. Jeśli została przydzielona w trakcie operacji na dokumencie, wszystkie pamięci na stosie `DeleteContents` jest najlepszym miejscem, aby cofnąć jej przydział.

> [!NOTE]
>  Nie należy cofnąć przydział danych dokumentu w destruktorze dokumentu. W przypadku aplikacji interfejsu SDI obiekt dokumentu może być ponownie używane.

Można zastąpić destruktor widoku można cofnąć alokacji wszelkie pamięci przydzielony na stosie.

## <a name="see-also"></a>Zobacz też

[Inicjowanie i oczyszczanie dokumentów i widoków](../mfc/initializing-and-cleaning-up-documents-and-views.md)

