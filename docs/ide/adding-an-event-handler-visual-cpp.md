---
title: Dodawanie obsługi zdarzeń (Visual C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.eventhandler.overview
dev_langs:
- C++
helpviewer_keywords:
- event handlers, adding
- properties [Visual Studio], MSBuild
- MSBuild, properties
ms.assetid: 050bebf0-a9e0-474b-905c-796fe5ac8fc3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 184161b22358f77845b5f7c4b6da0bb42f3ea15f
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "33324918"
---
# <a name="adding-an-event-handler-visual-c"></a>Dodawanie obsługi zdarzeń (Visual C++)
W edytorze zasobów, można dodać nowy program obsługi zdarzeń, lub edytować istniejące obsługi zdarzeń dotyczące używania kontroli okno dialogowe [Kreator obsługi zdarzeń](../ide/event-handler-wizard.md).  
  
 Zdarzenia można dodać do klasy wdrożenie przy użyciu — okno dialogowe [okna właściwości](/visualstudio/ide/reference/properties-window). Jeśli chcesz dodać zdarzenie do klasy innej niż klasa okno dialogowe, użyj kreatora program obsługi zdarzeń.  
  
### <a name="to-add-an-event-handler-to-a-dialog-box-control"></a>Aby dodać obsługę zdarzeń do formantu — okno dialogowe  
  
1.  Kliknij dwukrotnie plik zasobu okno dialogowe w [widok zasobów](../windows/resource-view-window.md) można otworzyć zasobu pole okna dialogowego z formantem w [Edytor okien dialogowych](../windows/dialog-editor.md).  
  
2.  Kliknij prawym przyciskiem myszy formant, dla którego chcesz obsługiwać zdarzenia z powiadomieniem.  
  
3.  W menu skrótów kliknij **Dodaj program obsługi zdarzeń** do wyświetlenia Kreator obsługi zdarzeń.  
  
4.  Wybierz zdarzenie w **typ komunikatu** pole, aby dodać do klasy wybrany w **listy klas** pole.  
  
5.  Zaakceptuj nazwę domyślną w **nazwa programu obsługi funkcji** pola lub podaj nazwę dowolnego.  
  
6.  Kliknij przycisk **Dodawanie i edytowanie** Dodaj program obsługi zdarzeń do projektu i Otwórz Edytor tekstu w nowej funkcji do Dodaj kod obsługi odpowiednie zdarzenie.  
  
     Jeśli program obsługi zdarzeń dla wybranej klasy już typ wybranego komunikatu **Dodawanie i edytowanie** jest niedostępny, i **edycji kodu** jest dostępna. Kliknij przycisk **edycji kodu** aby otworzyć Edytor tekstu w istniejącej funkcji.  
  
 Alternatywnie można dodać obsługi zdarzeń z [okna właściwości](/visualstudio/ide/reference/properties-window). Zobacz [Dodawanie obsługi zdarzeń dla formantów okna dialogowego](../windows/adding-event-handlers-for-dialog-box-controls.md) Aby uzyskać więcej informacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie funkcji z kreatorami kodów](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Dodawanie klasy](../ide/adding-a-class-visual-cpp.md)   
 [Dodawanie zmiennej członkowskiej](../ide/adding-a-member-variable-visual-cpp.md)   
 [Dodawanie funkcji członkowskiej](../ide/adding-a-member-function-visual-cpp.md)   
 [Handler komunikatów MFC](../mfc/reference/adding-an-mfc-message-handler.md)   
 [Nawigacja w strukturze klas](../ide/navigating-the-class-structure-visual-cpp.md)