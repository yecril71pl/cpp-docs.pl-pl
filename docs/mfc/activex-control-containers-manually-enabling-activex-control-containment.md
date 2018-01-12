---
title: "Kontenery formantów ActiveX: Ręczne Włączanie zawierania formantów ActiveX | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- AfxEnableControlContainer method [MFC]
- ActiveX control containers [MFC], enabling
- ActiveX controls [MFC], enabling containers
ms.assetid: 833bcde9-c9ad-4709-ad12-2fc2150fb6a5
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bf1ba1273a349f685b70fec6706b566c2b618f23
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="activex-control-containers-manually-enabling-activex-control-containment"></a>Kontenery kontrolek ActiveX: ręczne włączanie zawierania kontrolek ActiveX
Gdy Kreator aplikacji MFC jest używane do generowania aplikacji nie włączono obsługi formantu ActiveX, należy ręcznie dodać tę obsługę. W tym artykule opisano proces ręczne dodanie zawierania formantów ActiveX do istniejącej aplikacji kontenera OLE. Jeśli znasz z wyprzedzeniem mają obsługi formantów ActiveX w kontenerze sieci OLE, zapoznaj się z artykułem [Tworzenie kontenera kontrolki ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control-container.md).  
  
> [!NOTE]
>  W tym artykule wykorzystano opartych na oknach dialogowych ActiveX formantu kontenera projektu o nazwie kontenera i osadzonego formantu o nazwie OK jako przykłady w procedurach i kod.  
  
 Aby zapewnić obsługę formantów ActiveX, należy dodać do dwóch plików projektu na jeden wiersz kodu.  
  
-   Modyfikowanie w głównym oknie dialogowym `InitInstance` funkcji (dostępnej w KONTENERZE. CPP) przez Kreatora aplikacji MFC wywołania do [AfxEnableControlContainer](reference/ole-initialization.md#afxenablecontrolcontainer), jak w poniższym przykładzie:  
  
     [!code-cpp[NVC_MFCOleContainer#34](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_1.cpp)]  
    [!code-cpp[NVC_MFCOleContainer#35](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_2.cpp)]  
  
-   Dodaj następującą wartość do STDAFX Twojego projektu. Plik nagłówka H:  
  
     [!code-cpp[NVC_MFCOleContainer#36](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_3.h)]  
  
 Po wykonaniu tych kroków ponownie skompiluj projekt, klikając **kompilacji** na **kompilacji** menu.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontenery kontrolek ActiveX](../mfc/activex-control-containers.md)

