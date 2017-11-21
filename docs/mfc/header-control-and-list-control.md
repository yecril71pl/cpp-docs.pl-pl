---
title: "Formant nagłówka i formant listy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CListCtrl class [MFC], with CHeaderCtrl
- CListCtrl class [MFC], header controls
- CHeaderCtrl class [MFC], with CListCtrl
- controls [MFC], header
- header controls [MFC]
- header controls [MFC], list controls used with
ms.assetid: b20194b1-1a6b-4e2f-b890-1b3cca6650bc
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a3491ce0b61880d3dfa1969a38fb3b351c2a8903
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="header-control-and-list-control"></a>Kontrolka nagłówka i kontrolka listy
W większości przypadków użyje osadzony w formancie nagłówka [CListCtrl](../mfc/reference/clistctrl-class.md) lub [clistview —](../mfc/reference/clistview-class.md) obiektu. Istnieją jednak przypadkach, gdy obiekt formantu nagłówka oddzielne jest pożądane, takich jak manipulowania danymi uporządkowane wierszy lub kolumn, w [CView](../mfc/reference/cview-class.md)-pochodzi z obiektu. W takich sytuacjach należy większą kontrolę nad wyglądem i domyślne zachowanie formantu osadzonego nagłówka.  
  
 W typowych przypadkach, które mają formantu nagłówka, aby zapewnić standardowe, domyślne zachowanie, może zajść potrzeba użycia [CListCtrl](../mfc/reference/clistctrl-class.md) lub [clistview —](../mfc/reference/clistview-class.md) zamiast tego. Użyj `CListCtrl` kiedy ma funkcje domyślne formantu nagłówka, osadzonego w typowych formantu widoku listy. Użyj [clistview —](../mfc/reference/clistview-class.md) kiedy ma funkcje domyślne formantu nagłówka, osadzony w obiekcie widoku.  
  
> [!NOTE]
>  Kontrolka widoku listy zostanie utworzony przy użyciu tych kontrolek tylko obejmują formantu nagłówka wbudowanych `LVS_REPORT` stylu.  
  
 W większości przypadków wyglądu formantu osadzonego nagłówka może być modyfikowany przez zmienianie stylów formantu zawierającego widoku listy. Ponadto można uzyskać informacje o formancie nagłówka za pośrednictwem funkcji Członkowskich nadrzędnego formantu widoku listy. Jednak pełną kontrolę i dostępu do atrybutów i stylów formantu nagłówka osadzonych zalecane jest, czy można uzyskać wskaźnik do obiektu formantu nagłówka.  
  
 Obiekt formantu osadzonego nagłówka jest możliwy przy użyciu dowolnego **CListCtrl** lub `CListView` z wywołaniem do odpowiedniej klasy `GetHeaderCtrl` funkcję elementu członkowskiego. Poniższy kod ilustruje to:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#14](../mfc/codesnippet/cpp/header-control-and-list-control_1.cpp)]  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Używanie list obrazów z formantami nagłówka](../mfc/using-image-lists-with-header-controls.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [Formanty](../mfc/controls-mfc.md)

