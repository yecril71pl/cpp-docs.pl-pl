---
title: "Kontenery formantów ActiveX: Wyświetlanie i modyfikowanie właściwości kontrolki | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- properties [MFC], viewing and modifying
- ActiveX control containers [MFC], viewing and modifying properties
- resource editors, viewing and modifying ActiveX controls
- ActiveX controls [MFC], properties
- controls [MFC], properties
ms.assetid: 14ce5152-742b-4e0d-a9ab-c7b456e32918
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5e3a12f9d591cb94c8c16e7b9f22a4db0872e78f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="activex-control-containers-viewing-and-modifying-control-properties"></a>Kontenery kontrolek ActiveX: wyświetlanie i modyfikowanie właściwości kontrolki
Po wstawieniu formantu ActiveX w projekcie jest przydatne do wyświetlania i zmieniania właściwości jest obsługiwana przez kontrolkę ActiveX. W tym artykule omówiono sposób to zrobić za pomocą edytora zasobów języka Visual C++.  
  
 Jeśli aplikacja kontenera formantu ActiveX używa osadzonych formantów, można wyświetlać i modyfikować właściwości formantu w edytorze zasobów. Edytor zasobów służy także do ustawiania wartości właściwości w czasie projektowania. Edytor zasobów następnie automatycznie zapisuje te wartości w pliku zasobów projektu. Wszystkie wystąpienia kontrolki będzie miał zainicjowany do wartości tych właściwości.  
  
 W tej procedurze założono, że włożono formantu do projektu. Aby uzyskać informacje, zobacz [kontenery formantów ActiveX: Wstawianie formantu do aplikacji kontenera formantów](../mfc/inserting-a-control-into-a-control-container-application.md).  
  
 Pierwszym krokiem podczas przeglądania właściwości formantu jest można dodać wystąpienia formantu do projektu szablonu okna dialogowego.  
  
### <a name="to-view-the-properties-of-a-control"></a>Aby wyświetlić właściwości formantu  
  
1.  W widokach, otwórz **okna dialogowego** folderu.  
  
2.  Otwórz szablon okno główne okno dialogowe.  
  
3.  Wstaw formant ActiveX przy użyciu **Wstawianie formantu ActiveX** okno dialogowe. Aby uzyskać więcej informacji, zobacz [wyświetlanie i dodawanie formantów ActiveX do okna dialogowego](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).  
  
4.  W oknie dialogowym Wybierz formantu ActiveX.  
  
5.  W oknie właściwości, kliknij przycisk **właściwości** przycisku.  
  
 Użyj **właściwości** okno dialogowe do modyfikowania i testowania nowych właściwości natychmiast.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontenery kontrolek ActiveX](../mfc/activex-control-containers.md)

