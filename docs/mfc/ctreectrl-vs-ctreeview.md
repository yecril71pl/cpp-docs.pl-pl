---
title: "Ctreectrl — vs. CTreeView — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CTreeCtrl
- CTreeView
dev_langs:
- C++
helpviewer_keywords:
- tree view controls
- CTreeCtrl class [MFC], vs. CTreeView class [MFC]
- CTreeView class [MFC], vs. CTreeCtrl class [MFC]
- tree controls [MFC], and tree view
ms.assetid: bba5af25-103f-4b53-84d3-071bc9bd6494
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bb0c1b7a7bf73ab70bbccca6f2a9ccc2ab385516
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ctreectrl-vs-ctreeview"></a>Ctreectrl — vs. CTreeView —
MFC oferuje dwie klasy, które hermetyzują drzewa formantów: [CTreeCtrl](../mfc/reference/ctreectrl-class.md) i [CTreeView —](../mfc/reference/ctreeview-class.md). Każda klasa przydaje się w różnych sytuacjach.  
  
 Użyj `CTreeCtrl` gdy będziesz potrzebować formantu okna podrzędnego zwykły; na przykład w oknie dialogowym. Szczególnie należy użyć `CTreeCtrl` jeśli mają być innych formantów podrzędnych w oknie, tak jak typowe okno dialogowe.  
  
 Użyj `CTreeView` zużycia formant drzewa, aby działać tak jak widok okna architektury dokument/widok, a także formant drzewa. A `CTreeView` zajmie obszaru klienckiego całe okno ramowe lub okna podziału. Go będzie zmieniany automatycznie podczas zmiany rozmiaru jej okna nadrzędnego, a może przetwarzać komunikaty poleceń z menu, klawisze skrótów i pasków narzędzi. Ponieważ formant drzewa zawiera dane niezbędne do wyświetlania drzewa, odpowiedni obiekt dokumentu nie ma być skomplikowane — nawet można użyć [CDocument](../mfc/reference/cdocument-class.md) jako typ dokumentu w szablonie dokumentu.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

