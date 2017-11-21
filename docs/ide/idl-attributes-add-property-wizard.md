---
title: "Atrybuty IDL, Dodaj Kreatora właściwości | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.prop.idlattributes
dev_langs: C++
ms.assetid: 356ed666-79d0-4bd9-a5e7-cda679cbadbd
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8dd58ebd25c3b70b10ae3530577d70058bef5b86
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="idl-attributes-add-property-wizard"></a>Atrybuty IDL, Dodaj kreatora właściwości
Ta strona kreatora właściwości umożliwia określenie jakiekolwiek ustawienia języka (IDL) definicji interfejsu dla właściwości.  
  
 **Identyfikator**  
 Ustawia identyfikator numeryczny określające właściwość. Ta opcja nie jest dostępne dla właściwości niestandardowych interfejsów. Zobacz [identyfikator](http://msdn.microsoft.com/library/windows/desktop/aa367040) w *odwołania MIDL*.  
  
 **helpcontext**  
 Określa identyfikator kontekstu, która pozwala użytkownikowi oglądać informacje o tej właściwości w pliku pomocy. Zobacz [helpcontext](http://msdn.microsoft.com/library/windows/desktop/aa366851) w *odwołania MIDL*.  
  
 **HelpString —**  
 Określa ciąg znaków używany do opisania elementu, którego dotyczy. Domyślnie jest ustawiona "właściwość *nazwa właściwości*." Zobacz [HelpString —](http://msdn.microsoft.com/library/windows/desktop/aa366856) w *odwołania MIDL*.  
  
## <a name="other-options"></a>Inne opcje  
 Nie wszystkie opcje są dostępne dla wszystkich typów właściwości.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**powiązania**|Wskazuje, że właściwość obsługuje powiązanie danych. Zobacz [powiązania](http://msdn.microsoft.com/library/windows/desktop/aa366738) w *odwołania MIDL*. Do wykonania podstawowych właściwości ta opcja jest ustawieniem domyślnym i jest niezmienne.|  
|**defaultbind —**|Wskazuje, że to jednej, które można powiązać właściwości najlepiej reprezentuje obiekt. Zobacz [defaultbind —](http://msdn.microsoft.com/library/windows/desktop/aa366790) w *odwołania MIDL*.|  
|**displaybind —**|Wskazuje, że ta właściwość powinna być wyświetlana użytkownikowi jak możliwa do powiązania. Zobacz [displaybind —](http://msdn.microsoft.com/library/windows/desktop/aa366804) w *odwołania MIDL*.|  
|**immediatebind —**|Wskazuje, że bazy danych zostanie niezwłocznie powiadomiona o wszystkich zmianach tej właściwości obiektu powiązanego z danymi. Zobacz [immediatebind —](http://msdn.microsoft.com/library/windows/desktop/aa367045) w *odwołania MIDL*.|  
|**defaultcollelem —**|Wskazuje, że właściwość jest funkcja dostępu do elementu domyślnej kolekcji. Zobacz [defaultcollelem —](http://msdn.microsoft.com/library/windows/desktop/aa366792) w *odwołania MIDL*.|  
|**nonbrowsable —**|Znaczniki elementu członkowskiego interfejsu lub dispinterface nie powinien być wyświetlany w przeglądarce właściwości. Zobacz [nonbrowsable —](http://msdn.microsoft.com/library/windows/desktop/aa367117) w *odwołania MIDL*.|  
|**requestedit —**|Wskazuje, że właściwość obsługuje **OnRequestEdit** powiadomień można znaleźć [requestedit —](http://msdn.microsoft.com/library/windows/desktop/aa367155) w *odwołania MIDL*. Do wykonania podstawowych właściwości ta opcja jest ustawieniem domyślnym i jest niezmienne.|  
|**źródło**|Wskazuje, że element członkowski właściwości jest źródłem zdarzeń. Zobacz [źródła](http://msdn.microsoft.com/library/windows/desktop/aa367166) w *odwołania MIDL*.|  
|**ukryte**|Wskazuje, że właściwość istnieje, ale nie powinien być wyświetlany w przeglądarce zorientowanej na użytkownika. Zobacz [ukryte](http://msdn.microsoft.com/library/windows/desktop/aa366861) w *odwołania MIDL*.|  
|**ograniczone**|Określa, że właściwość nie może być wywoływana arbitralnie. Zobacz [ograniczeniami](http://msdn.microsoft.com/library/windows/desktop/aa367157) w *odwołania MIDL*.|  
|`local`|Określa kompilatorowi MIDL, właściwość nie jest zdalna. Zobacz [lokalnego](http://msdn.microsoft.com/library/windows/desktop/aa367071) w *odwołania MIDL*.|  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie właściwości](../ide/adding-a-property-visual-cpp.md)   
 [Nazwy, Dodaj Kreatora właściwości](../ide/names-add-property-wizard.md)   
 [Implementowanie interfejsu](../ide/implementing-an-interface-visual-cpp.md)   
 [Właściwości podstawowe](../ide/stock-properties.md)