---
title: "Arkusze właściwości i strony właściwości w MFC | Dokumentacja firmy Microsoft"
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
- property pages [MFC], MFC
- controls [MFC], property sheets
- property sheets, MFC
- tab dialog boxes
ms.assetid: e1bede2b-0285-4b88-a052-0f8a372807a2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 24a66bf9e062e43225827afdbb0bba45511c5f13
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="property-sheets-and-property-pages-in-mfc"></a>Arkusze właściwości i strony właściwości w MFC
Arkusz właściwości, znanej także jako okno dialogowe kartę, to okno dialogowe, który zawiera strony właściwości. Każdej strony właściwości jest oparta na zasobu szablonu okna dialogowego i zawiera formanty. Na stronie będzie znajdował się z karty w górnej części. Karcie nazwy strony i wskazuje jej celem. Użytkownicy kartę w arkuszu właściwości, aby wybrać zestaw kontrolek.  
  
 Użyj strony do formantów w arkuszu właściwości w łatwy do rozpoznania zestawów. Arkusz właściwości zawartych w niej zwykle ma kilka formantów własnych. Te dotyczą wszystkich stron.  
  
 Arkusze właściwości są oparte na klasie [cpropertysheet —](../mfc/reference/cpropertysheet-class.md). Strony właściwości są oparte na klasie [cpropertypage —](../mfc/reference/cpropertypage-class.md).  
  
 Arkusz właściwości jest specjalnym rodzajem okno dialogowe, który zazwyczaj jest używane do modyfikowania atrybutów niektórych obiektu zewnętrznego, takie jak bieżące zaznaczenie w widoku. Arkusz właściwości ma trzy główne części: okno dialogowe zawierające jeden lub więcej stron właściwości wyświetlane pojedynczo i karty w górnej części każdej stronie, które użytkownik klika, aby wybrać tę stronę. Arkusze właściwości są przydatne w sytuacjach, w którym znajduje się kilka podobne grupy ustawień lub opcji, aby zmienić. Arkusz właściwości grupy informacji w sposób łatwy do zrozumienia sposób.  
  
> [!NOTE]
>  Jeśli próbujesz Pokaż arkusz właściwości przy użyciu `CPropertySheet::DoModal`, system może generować wyjątkach pierwszej szansy. Ten wyjątek występuje, ponieważ system próbuje zmienić [Style okna](../mfc/reference/styles-used-by-mfc.md#window-styles) obiektu przed utworzeniem obiektu. Aby uzyskać więcej informacji na temat tego wyjątku i jak zapobiec lub jego obsługa, zobacz [CPropertySheet::DoModal](../mfc/reference/cpropertysheet-class.md#domodal).  
  
## <a name="see-also"></a>Zobacz też  
 [Arkusze właściwości](../mfc/property-sheets-mfc.md)

