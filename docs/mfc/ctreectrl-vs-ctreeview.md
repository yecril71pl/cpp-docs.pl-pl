---
title: "Ctreectrl — vs. CTreeView — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CTreeCtrl
- CTreeView
dev_langs: C++
helpviewer_keywords:
- tree view controls
- CTreeCtrl class [MFC], vs. CTreeView class [MFC]
- CTreeView class [MFC], vs. CTreeCtrl class [MFC]
- tree controls [MFC], and tree view
ms.assetid: bba5af25-103f-4b53-84d3-071bc9bd6494
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b5a0dfd4f7b658cc585972ace1335a80b9bbd93a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ctreectrl-vs-ctreeview"></a>Ctreectrl — vs. CTreeView —
MFC oferuje dwie klasy, które hermetyzują drzewa formantów: [CTreeCtrl](../mfc/reference/ctreectrl-class.md) i [CTreeView —](../mfc/reference/ctreeview-class.md). Każda klasa przydaje się w różnych sytuacjach.  
  
 Użyj `CTreeCtrl` gdy będziesz potrzebować formantu okna podrzędnego zwykły; na przykład w oknie dialogowym. Szczególnie należy użyć `CTreeCtrl` jeśli mają być innych formantów podrzędnych w oknie, tak jak typowe okno dialogowe.  
  
 Użyj `CTreeView` zużycia formant drzewa, aby działać tak jak widok okna architektury dokument/widok, a także formant drzewa. A `CTreeView` zajmie obszaru klienckiego całe okno ramowe lub okna podziału. Go będzie zmieniany automatycznie podczas zmiany rozmiaru jej okna nadrzędnego, a może przetwarzać komunikaty poleceń z menu, klawisze skrótów i pasków narzędzi. Ponieważ formant drzewa zawiera dane niezbędne do wyświetlania drzewa, odpowiedni obiekt dokumentu nie ma być skomplikowane — nawet można użyć [CDocument](../mfc/reference/cdocument-class.md) jako typ dokumentu w szablonie dokumentu.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Formanty](../mfc/controls-mfc.md)

