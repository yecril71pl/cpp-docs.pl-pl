---
title: Dodawanie właściwości (Visual C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interfaces, adding properties
- properties [C++], adding to interfaces
ms.assetid: 37bd4db7-efd3-4faa-87ad-64902ed16a36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 00b19fa7166e6edad05d729c5a738a2a827086ae
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43212798"
---
# <a name="adding-a-property-visual-c"></a>Dodawanie właściwości (Visual C++)
Możesz użyć [Kreator dodawania właściwości](../ide/names-add-property-wizard.md) Aby dodać metodę do interfejsu w projekcie.  
  
### <a name="to-add-a-property-to-your-object"></a>Aby dodać właściwość do obiektu  
  
1.  W [Widok klas](https://msdn.microsoft.com/8d7430a9-3e33-454c-a9e1-a85e3d2db925), kliknij prawym przyciskiem myszy nazwę interfejsu, do którego chcesz dodać właściwość.  
  
    > [!NOTE]
    >  Można również dodać właściwości do dispinterfaces, który, chyba że projekt jest przypisane, są zagnieżdżone w obrębie węzła biblioteki.  
  
2.  W menu skrótów kliknij **Dodaj**, a następnie kliknij przycisk **Dodaj właściwość**.  
  
3.  W [Kreator dodawania właściwości](../ide/names-add-property-wizard.md), podaj informacje, aby utworzyć właściwość.  
  
4.  Określ jakiekolwiek ustawienia interfejsu definicja języka (IDL) dla właściwości w [atrybuty IDL](../ide/idl-attributes-add-property-wizard.md) strony kreatora.  
  
5.  Kliknij przycisk **Zakończ** można dodać właściwości.  
  
 **Uzyskać** i `Put` metody, właściwości są wyświetlane jako dwie ikony w widoku klas w obszarze interfejs, w którym jest zdefiniowana. Możesz kliknąć dwukrotnie albo ikonę, aby wyświetlić deklaracja właściwości w pliku .idl.  
  
-   Interfejsy ATL **uzyskać** i **umieścić** funkcje są dodawane do pliku .cpp i odwołania do tych funkcji są dodawane do pliku .h.  
  
-   Dla dispinterfaces MFC, jeśli zostanie wybrana **zmiennej składowej** jako typ implementacji metody i zmienna są dodawane do klasy, która implementuje go. Jeśli wybierzesz **metod Get/Set** jako typ implementacji dwie metody są dodawane do klasy, która implementuje go.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie interfejsu COM](../ide/creating-a-com-interface-visual-cpp.md)   
 [Edytowanie interfejsu COM](../ide/editing-a-com-interface.md)   
 [Model Component Object Model](/windows/desktop/com/the-component-object-model)   
 [Wskaźniki interfejsu i interfejsy](/windows/desktop/com/interface-pointers-and-interfaces)