---
title: "Deklarowanie zmiennej oparte na nowej klasie formantów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.classes.control.variable
dev_langs:
- C++
helpviewer_keywords:
- variables [MFC], control classes
- control classes [MFC], variables
- classes [MFC], declaring variables based on
ms.assetid: 5722dc38-c0eb-40bd-93da-67a808140d03
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5aa98f815d9f9322c11d4256c13c0c7a42b4ab66
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="declaring-a-variable-based-on-your-new-control-class"></a>Deklarowanie zmiennej opartej na nowej klasie formantów
Po utworzeniu klasę formantu MFC można zadeklarować zmiennej na ich podstawie. Zapewnienie kontekst nową zmienną, musi otworzyć edytora okien dialogowych i edytować okno dialogowe, w której chcesz użyć do ponownego użycia formantu. Ponadto okno dialogowe musi mieć już skojarzone z nią klasy. Aby uzyskać informacje na temat używania edytora okien dialogowych, zobacz [Edytor okien dialogowych](../../windows/dialog-editor.md).  
  
### <a name="to-declare-a-variable-based-on-your-reusable-class"></a>Deklarowanie zmiennej opartej na klasie wielokrotnego użytku  
  
1.  Podczas edycji okno dialogowe, przeciągnij formant tego samego typu jako klasa podstawowa nowego formantu z pasek narzędzi kontrolek na oknie dialogowym.  
  
2.  Umieść wskaźnik myszy nad formantem porzucone.  
  
3.  Naciskaj klawisz CTRL, kliknij dwukrotnie formant.  
  
     [Dodać zmiennej członka](../../ide/add-member-variable-wizard.md) zostanie wyświetlone okno dialogowe.  
  
4.  W **dostępu** wybierz prawidłowy dostęp dla formantu.  
  
5.  Kliknij przycisk **zmienna sterująca** pole wyboru.  
  
6.  W **nazwa zmiennej** wpisz nazwę.  
  
7.  W obszarze **kategorii**, kliknij przycisk **kontroli**.  
  
8.  W **Identyfikatora formantu** listy, wybierz formant, który został dodany. **Typ zmiennej** listy powinien być wyświetlany poprawnego typu zmienną i **kontroli typem** pole powinien być wyświetlany typu poprawne formantu.  
  
9. W **komentarz** Dodaj wszelkie komentarz ma być wyświetlana w kodzie.  
  
10. Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Mapowanie komunikatów na funkcje](../../mfc/reference/mapping-messages-to-functions.md)   
 [Dodawanie funkcji z kreatorami kodów](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)   
 [Dodawanie funkcji członkowskiej](../../ide/adding-a-member-function-visual-cpp.md)   
 [Dodawanie zmiennej członkowskiej](../../ide/adding-a-member-variable-visual-cpp.md)   
 [Zastępowanie funkcji wirtualnych](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Handler komunikatów MFC](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [Nawigacja w strukturze klas](../../ide/navigating-the-class-structure-visual-cpp.md)
