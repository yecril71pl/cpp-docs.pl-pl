---
title: Zastępowanie funkcji wirtualnych (Visual C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.virtualfunc.override
dev_langs:
- C++
helpviewer_keywords:
- virtual functions, overriding
- base classes, overriding virtual functions defined in
- Properties window, overriding virtual functions in
ms.assetid: 2d8c76f2-7a6b-4c9c-8de5-4282ce7755b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d8580d27442b0cae7e343a568beaa9aeae500461
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "33337746"
---
# <a name="overriding-a-virtual-function-visual-c"></a>Zastępowanie funkcji wirtualnych (Visual C++)
Można zastąpić funkcji wirtualnych zdefiniowanych w klasie podstawowej z programu Visual Studio [okna właściwości](/visualstudio/ide/reference/properties-window).  
  
### <a name="to-override-a-virtual-function-in-the-properties-window"></a>Aby przesłonić funkcję wirtualną w oknie właściwości  
  
1.  W widoku klas kliknij klasy.  
  
2.  Kliknij w oknie właściwości **zastępuje** przycisku.  
  
    > [!NOTE]
    >  **Zastępuje** przycisk jest dostępny po wybraniu nazwy klasy w widoku klas lub po kliknięciu w oknie źródła.  
  
     Po lewej stronie wymieniono funkcje wirtualne. Jeśli nazwa funkcji wirtualnej jest także wyświetlany w prawej kolumnie, zastąpienia już została zaimplementowana.  
  
3.  Jeśli funkcja ma nie zastępuj, następnie kliknij komórkę w prawej kolumnie w oknie właściwości, aby wyświetlić sugerowane nazwy funkcji zastępują jako \<Dodaj >*FuncName*.  
  
4.  Kliknij, aby dodać kod klasy zastępczej dla funkcji.  
  
5.  Aby edytować zastępowanie funkcji, kliknij dwukrotnie nazwę funkcji w widoku klas i edytować kod w oknie źródła.  
  
 Aby usunąć zastąpienia, kliknij nazwę funkcji zastąpienia w prawej kolumnie, a następnie wybierz \<usunąć >*FuncName*. Kod funkcji jest oznaczone jako komentarz.  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie funkcji z kreatorami kodów](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Dodawanie klasy](../ide/adding-a-class-visual-cpp.md)   
 [Dodawanie funkcji członkowskiej](../ide/adding-a-member-function-visual-cpp.md)   
 [Dodawanie zmiennej członkowskiej](../ide/adding-a-member-variable-visual-cpp.md)   
 [Handler komunikatów MFC](../mfc/reference/adding-an-mfc-message-handler.md)   
 [Nawigacja w strukturze klas](../ide/navigating-the-class-structure-visual-cpp.md)