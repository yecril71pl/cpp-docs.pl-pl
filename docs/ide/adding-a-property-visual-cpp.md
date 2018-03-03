---
title: "Dodawanie właściwości (Visual C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- interfaces, adding properties
- properties [C++], adding to interfaces
ms.assetid: 37bd4db7-efd3-4faa-87ad-64902ed16a36
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 33fc8c3b5528c0ced4e0d402aec48791b7fbcb9a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="adding-a-property-visual-c"></a>Dodawanie właściwości (Visual C++)
Można użyć [Dodaj Kreatora właściwości](../ide/names-add-property-wizard.md) dodanie metody interfejsu w projekcie.  
  
### <a name="to-add-a-property-to-your-object"></a>Aby dodać właściwości do obiektu  
  
1.  W [widoku klasy](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), kliknij prawym przyciskiem myszy nazwę interfejsu, do którego chcesz dodać właściwości.  
  
    > [!NOTE]
    >  Można również dodać właściwości do dispinterfaces, który, chyba że projekt jest przypisane, są zagnieżdżone w obrębie węzła biblioteki.  
  
2.  W menu skrótów kliknij **Dodaj**, a następnie kliknij przycisk **Dodaj właściwość**.  
  
3.  W [Dodaj Kreatora właściwości](../ide/names-add-property-wizard.md), podaj informacje, aby utworzyć właściwość.  
  
4.  Określ jakiekolwiek ustawienia języka (IDL) definicji interfejsu dla właściwości w [atrybuty IDL](../ide/idl-attributes-add-property-wizard.md) stronie kreatora.  
  
5.  Kliknij przycisk **Zakończ** można dodać właściwości.  
  
 **Uzyskać** i `Put` metody, właściwości są wyświetlane jako dwa ikony w widoku klas, w obszarze interfejsu, w którym jest zdefiniowana. Możesz kliknąć dwukrotnie albo ikonę, aby wyświetlić deklaracja właściwości w pliku .idl.  
  
-   Dla interfejsów ATL **uzyskać** i **Put** funkcje są dodawane do pliku .cpp, a odwołania do tych funkcji są dodawane do pliku .h.  
  
-   Dla dispinterfaces MFC, w przypadku wybrania **zmiennej członkowskiej** jako typ implementacji metody i zmienna są dodawane do klasy, która implementuje go. W przypadku wybrania **metod Get/Set** jako typ implementacji dwie metody są dodawane do klasy, która implementuje go.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie interfejsu COM](../ide/creating-a-com-interface-visual-cpp.md)   
 [Edytowanie interfejsu COM](../ide/editing-a-com-interface.md)   
 [Model Component Object Model](http://msdn.microsoft.com/library/windows/desktop/ms694363)   
 [Wskaźniki interfejsu i interfejsy](http://msdn.microsoft.com/library/windows/desktop/ms688484)