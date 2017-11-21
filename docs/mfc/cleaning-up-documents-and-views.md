---
title: "Oczyszczanie dokumentów i widoków | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- views [MFC], cleaning up
- documents [MFC], cleaning up
- documents [MFC], closing
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f9bb1cbcb58e2693b33693b390a09d3826c77cfd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cleaning-up-documents-and-views"></a>Oczyszczanie dokumentów i widoków
Gdy dokument jest zamykany, struktura najpierw wywołuje jego [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) funkcję elementu członkowskiego. Jeśli przydzielone wszystkie pamięci na stercie w trakcie operacji dokumentu `DeleteContents` jest najlepszym miejscem, aby zwolnić go.  
  
> [!NOTE]
>  Nie należy deallocate dane dokumentu w destruktorze dokumentu. W przypadku aplikacji SDI obiektu dokumentu może zostać użyty ponownie.  
  
 Można zastąpić destruktora widoku, aby zwolnić wszystkie przydzielone na stercie pamięci.  
  
## <a name="see-also"></a>Zobacz też  
 [Inicjowanie i oczyszczanie dokumentów i widoków](../mfc/initializing-and-cleaning-up-documents-and-views.md)

