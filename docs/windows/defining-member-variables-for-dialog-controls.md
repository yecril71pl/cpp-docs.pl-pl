---
title: "Definiowanie zmiennych Członkowskich dla formantów okna dialogowego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- member variables, defining for controls
- variables, dialog box control member variables
- controls [C++], member variables
- Dialog editor, defining member variables for controls
ms.assetid: 84347c63-c33c-4b04-91f5-6d008c45ba58
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f81b0d124db2a28b8d38c1a79d7569d8e46742b3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="defining-member-variables-for-dialog-controls"></a>Definiowanie zmiennych członkowskich dla formantów okna dialogowego
Do zdefiniowania zmiennej elementu członkowskiego dla każdego formantu okno dialogowe z wyjątkiem przycisków, używając następującej metody.  
  
> [!NOTE]
>  Ten artykuł dotyczy tylko dla formantów okna dialogowego w projekcie MFC. Projekty ATL należy używać **nowe komunikaty systemu Windows i procedury obsługi zdarzeń** okno dialogowe.  
  
### <a name="to-define-a-member-variable-for-a-non-button-dialog-box-control"></a>Aby zdefiniować zmienną członkowską dla formantu pola dialogowe (z systemem innym niż przycisk)  
  
1.  W [Edytor okien dialogowych](../windows/dialog-editor.md), zaznacz kontrolkę.  
  
2.  Podczas naciskając klawisz **CTRL** klucza, kliknij dwukrotnie kontrolka okna dialogowego.  
  
     [Kreator dodawania zmiennej elementu członkowskiego](../ide/add-member-variable-wizard.md) pojawi się.  
  
3.  Wpisz odpowiednie informacje w **dodać zmiennej członka** kreatora. Aby uzyskać więcej informacji, zobacz [wymiana danych okna dialogowego](../mfc/dialog-data-exchange.md).  
  
4.  Kliknij przycisk **OK** aby powrócić do edytora okien dialogowych.  
  
    > [!TIP]
    >  Aby przejść z dowolnym kontrolka okna dialogowego do swojego istniejącego programu obsługi, kliknij dwukrotnie formant.  
  

  
 Można również użyć **zmienne Członkowskie** karcie **Kreator klas MFC** Aby dodać nowe zmienne Członkowskie określonej klasy i wyświetlić te, które zostały już zdefiniowane.  
  
 Wymagania  
  
 MFC  
  
## <a name="see-also"></a>Zobacz też  
 [Mapowanie komunikatów na funkcje](../mfc/reference/mapping-messages-to-functions.md)   
 [Dodawanie funkcji z kreatorami kodów](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Kreator klas MFC](../mfc/reference/mfc-class-wizard.md)   
 [Dodawanie klasy](../ide/adding-a-class-visual-cpp.md)   
 [Dodawanie funkcji członkowskiej](../ide/adding-a-member-function-visual-cpp.md)   
 [Dodawanie zmiennej członkowskiej](../ide/adding-a-member-variable-visual-cpp.md)   
 [Zastępowanie funkcji wirtualnych](../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Handler komunikatów MFC](../mfc/reference/adding-an-mfc-message-handler.md)

