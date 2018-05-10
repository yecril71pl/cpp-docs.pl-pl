---
title: Definiowanie zmiennych Członkowskich dla formantów okna dialogowego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- member variables, defining for controls
- variables, dialog box control member variables
- controls [C++], member variables
- Dialog editor, defining member variables for controls
ms.assetid: 84347c63-c33c-4b04-91f5-6d008c45ba58
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8ba8fc95290ecb90557203be2b6ab4cce18b91e3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
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

