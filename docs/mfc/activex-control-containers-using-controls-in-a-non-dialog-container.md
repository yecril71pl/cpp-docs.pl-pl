---
title: "Kontenery formantów ActiveX: Używanie formantów w kontenerze z systemem innym niż okno dialogowe | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Create method [MFC], ActiveX controls
- CreateControl method [MFC]
- ActiveX controls [MFC], creating
- ActiveX control containers [MFC], non-dialog containers
- ActiveX control containers [MFC], inserting controls
ms.assetid: 46f195b0-b8ca-4409-8cca-fbfaf2c9ab9f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c380d0a525c2f026054ebae1812450c4d4634c1e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="activex-control-containers-using-controls-in-a-non-dialog-container"></a>Kontenery kontrolek ActiveX: używanie kontrolek w kontenerze innym niż okno dialogowe
W niektórych aplikacjach, takich jak SDI lub MDI aplikacji można osadzić formantu w oknie aplikacji. **Utwórz** funkcji członkowskiej klasy otoki wstawiane przez Visual C++, można utworzyć wystąpienia formantu dynamicznie, bez konieczności dla okna dialogowego.  
  
 **Utwórz** funkcji członkowskiej ma następujące parametry:  
  
 `lpszWindowName`  
 Wskaźnik do tekst do wyświetlenia w właściwości Text lub Caption formantu (jeśli istnieje).  
  
 `dwStyle`  
 Style systemu Windows. Aby uzyskać pełną listę, zobacz [CWnd::CreateControl](../mfc/reference/cwnd-class.md#createcontrol).  
  
 `rect`  
 Określa rozmiar i położenie formantu.  
  
 `pParentWnd`  
 Określa okno nadrzędne kontrolki, zwykle `CDialog`. Nie może być **NULL**.  
  
 `nID`  
 Określa identyfikator formantu i może służyć przez kontener do odwoływania się do formantu.  
  
 Jednym z przykładów przy użyciu tej funkcji można dynamicznie utworzyć formantu ActiveX byłoby w widoku formularza SDI aplikacji. Następnie można utworzyć wystąpienia formantu w `WM_CREATE` obsługi aplikacji.  
  
 Na przykład `CMyView` jest klasa widoku głównego `CCirc` klasy otoki i okólnik H jest nagłówka (. H) pliku klasy otoki.  
  
 Implementacja tej funkcji jest procesem czterech kroków.  
  
### <a name="to-dynamically-create-an-activex-control-in-a-non-dialog-window"></a>Można dynamicznie utworzyć formantu ActiveX w oknie dialogowym z systemem innym niż  
  
1.  Wstaw okólnik H w CMYVIEW. H, bezpośrednio przed `CMyView` definicji klasy:  
  
     [!code-cpp[NVC_MFC_AxCont#12](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_1.h)]  
  
2.  Dodaj zmienną członkowską (typu `CCirc`) do sekcji chronionych `CMyView` znajduje się w CMYVIEW definicji klasy. H:  
  
     [!code-cpp[NVC_MFC_AxCont#13](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_2.h)]  
    [!code-cpp[NVC_MFC_AxCont#14](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_3.h)]  
  
3.  Dodaj `WM_CREATE` obsługi wiadomości do klasy `CMyView`.  
  
4.  W funkcji obsługi `CMyView::OnCreate`, wywoływania formantu `Create` funkcji przy użyciu **to** wskaźnika jako okno nadrzędne:  
  
     [!code-cpp[NVC_MFC_AxCont#15](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_4.cpp)]  
  
5.  Skompiluj ponownie projekt. Formant OK zostanie utworzony dynamicznie zawsze, gdy jest tworzony widok aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontenery kontrolek ActiveX](../mfc/activex-control-containers.md)

