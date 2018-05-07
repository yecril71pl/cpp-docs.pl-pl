---
title: Inicjowanie i oczyszczanie dokumentów i widoków | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- initializing documents [MFC]
- views [MFC], cleaning up
- documents [MFC], initializing
- documents [MFC], cleaning up
- views [MFC], initializing
- initializing objects [MFC], document objects
- document objects [MFC], life cycle of
- initializing views [MFC]
ms.assetid: 95d6f09b-a047-4079-856a-ae7d0548e9d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0f59dcfbdac4a2d5da732c5e7f8cfc78083bf843
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="initializing-and-cleaning-up-documents-and-views"></a>Inicjowanie i oczyszczanie dokumentów i widoków
Inicjowanie i oczyszczanie po dokumentów i widoków, skorzystaj z poniższych wskazówek:  
  
-   Struktura MFC inicjuje dokumentów i widoków; należy zainicjować danych, które można dodawać do nich.  
  
-   Platformę czyści jako dokumenty i widoki Zamknij; Musisz cofnąć wszystkie pamięci, które przydzielone na stercie z wewnątrz funkcji Członkowskich tych dokumentów i widoków.  
  
> [!NOTE]
>  Odwołaj ten inicjowania dla całej aplikacji odbywa się najlepiej w zastąpienia z [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) funkcji członkowskiej klasy `CWinApp`, i czyszczenia dla całej aplikacji najlepiej pozostawić w zastąpienia z `CWinApp`funkcji członkowskiej [ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance).  
  
 Cykl życia dokumentu (i jego okno ramowe i widoku lub widoków) w interfejsie MDI aplikacji jest następujący:  
  
1.  Podczas tworzenia dynamicznej wywołania konstruktora dokumentu.  
  
2.  Dla każdego nowego dokumentu, dokument [OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument) lub [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) jest wywoływana.  
  
3.  Użytkownik wchodzi w interakcję z dokumentu przez cały cykl jej życia. Zwykle dzieje się jako użytkownik pracuje w danych dokumentu za pośrednictwem widoku, wybierając i edytowanie danych. Widok przekazuje zmiany do dokumentu dla magazynu i aktualizowanie z innymi widokami. W tym czasie dokument programu i widok może obsługiwać poleceń.  
  
4.  Wywołania framework [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) do usuwania danych specyficznych dla dokumentu.  
  
5.  Destruktor dokumentu jest wywoływany.  
  
 W aplikacji SDI kroku 1 jest wykonywane raz, po pierwszym utworzeniu dokumentu. Następnie kroki od 2 do 4 są wykonywane wielokrotnie zawsze, gdy zostanie otwarty nowy dokument. Nowy dokument ponownie używa istniejący obiekt dokumentu. Na koniec krok 5 odbywa się podczas kończenia aplikacji.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Inicjowanie dokumentów i widoków](../mfc/initializing-documents-and-views.md)  
  
-   [Oczyszczanie dokumentów i widoków](../mfc/cleaning-up-documents-and-views.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura dokument/widok](../mfc/document-view-architecture.md)

