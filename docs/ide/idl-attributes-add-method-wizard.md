---
title: Atrybuty IDL, Kreator dodawania metody | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.method.idlattrib
dev_langs: C++
helpviewer_keywords:
- Add Method Wizard [C++]
- IDL attributes, Add Method Wizard
ms.assetid: f80c3bc1-b515-4d6c-83ee-98c2c21ba902
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9792f8b7758ff5a1e5742b6643d9f73931bce6f9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="idl-attributes-add-method-wizard"></a>Atrybuty IDL, Kreator dodawania metody
Ta strona kreatora dodawania metody umożliwia Określ jakiekolwiek ustawienia języka (IDL) definicji interfejsu dla metody.  
  
 **id**  
 Ustawia identyfikator numeryczny, który identyfikuje metodę. Zobacz [identyfikator](http://msdn.microsoft.com/library/windows/desktop/aa367040) w *odwołania MIDL*.  
  
 To pole jest niedostępna dla niestandardowych interfejsów i nie jest dostępna dla MFC dispinterfaces.  
  
 **call_as**  
 Określa nazwę metody zdalnego, do którego ta metoda lokalne mogą być mapowane. Zobacz [call_as](http://msdn.microsoft.com/library/windows/desktop/aa366748) w *odwołania MIDL*.  
  
 Nie jest dostępna dla MFC dispinterfaces.  
  
 **helpcontext**  
 Określa identyfikator kontekstu, która pozwala użytkownikowi oglądać informacje o tej metodzie w pliku pomocy. Zobacz [helpcontext](http://msdn.microsoft.com/library/windows/desktop/aa366851) w *odwołania MIDL*.  
  
 Nie jest dostępna dla MFC dispinterfaces.  
  
 **helpstring**  
 Określa ciąg znaków używany do opisania elementu, którego dotyczy. Domyślnie jest ustawiona "metody *nazwę metody*." Zobacz [HelpString —](http://msdn.microsoft.com/library/windows/desktop/aa366856) w *odwołania MIDL*.  
  
 Nie jest dostępna dla MFC dispinterfaces.  
  
 **Dodatkowe atrybuty**  
 Nie jest dostępna dla MFC dispinterfaces.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|**hidden**|Wskazuje, że metoda istnieje, ale nie powinien być wyświetlany w przeglądarce zorientowanej na użytkownika. Zobacz [ukryte](http://msdn.microsoft.com/library/windows/desktop/aa366861) w *odwołania MIDL*.|  
|**źródło**|Wskazuje, że członkiem metoda jest źródłem zdarzeń. Zobacz [źródła](http://msdn.microsoft.com/library/windows/desktop/aa367166) w *odwołania MIDL*.|  
|`local`|Określa kompilatorowi MIDL, metoda nie jest zdalny. Zobacz [lokalnego](http://msdn.microsoft.com/library/windows/desktop/aa367071) w *odwołania MIDL*.|  
|**restricted**|Określa, że metoda nie może być wywoływana arbitralnie. Zobacz [ograniczeniami](http://msdn.microsoft.com/library/windows/desktop/aa367157) w *odwołania MIDL*.|  
|**vararg**|Określa, że metoda przyjmuje zmienną liczbę argumentów. Aby to zrobić, ostatni argument musi być bezpieczną tablicą o **VARIANT** typu, który zawiera wszystkie pozostałe argumenty. Zobacz [vararg](http://msdn.microsoft.com/library/windows/desktop/aa367304) w *odwołania MIDL*.|  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie metody](../ide/adding-a-method-visual-cpp.md)   
 [Kreator dodawania metody](../ide/add-method-wizard.md)