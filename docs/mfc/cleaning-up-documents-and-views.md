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
ms.openlocfilehash: 2dfe54c13db6f44bc70289380ae5f50d99c3722b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cleaning-up-documents-and-views"></a>Oczyszczanie dokumentów i widoków
Gdy dokument jest zamykany, struktura najpierw wywołuje jego [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) funkcję elementu członkowskiego. Jeśli przydzielone wszystkie pamięci na stercie w trakcie operacji dokumentu `DeleteContents` jest najlepszym miejscem, aby zwolnić go.  
  
> [!NOTE]
>  Nie należy deallocate dane dokumentu w destruktorze dokumentu. W przypadku aplikacji SDI obiektu dokumentu może zostać użyty ponownie.  
  
 Można zastąpić destruktora widoku, aby zwolnić wszystkie przydzielone na stercie pamięci.  
  
## <a name="see-also"></a>Zobacz też  
 [Inicjowanie i oczyszczanie dokumentów i widoków](../mfc/initializing-and-cleaning-up-documents-and-views.md)

