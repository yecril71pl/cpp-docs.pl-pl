---
title: Kojarzenie poleceń Menu z tekstem paska stanu w aplikacjach MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- status bars, associating menu items
- menus, status bar text
ms.assetid: 757c0e02-bc97-493f-bccd-6cc6887ebc64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 17326bdb8fe01c9ad329db0a6c7e8178fdbb25e7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33864245"
---
# <a name="associating-menu-commands-with-status-bar-text-in-mfc-applications"></a>Kojarzenie poleceń menu z tekstem paska stanu w aplikacjach MFC
Aplikacja może wyświetlać tekst opisowy dla poszczególnych poleceń menu, które użytkownik może wybrać. Można to zrobić, przypisując ciąg tekstowy do każdego menu polecenie za pomocą **monitu** właściwości w oknie właściwości. Jeśli w ciągu [tabeli ciągów](../windows/string-editor.md) których identyfikator jest taki sam jak polecenia, aplikacji MFC zostanie automatycznie wyświetlona tego zasobu ciągu na pasku stanu w uruchomionej aplikacji, gdy użytkownik znajduje się nad elementem menu.  
  
### <a name="to-associate-a-menu-command-with-a-status-bar-text-string"></a>Aby skojarzyć polecenia menu z stanu paska ciąg tekstowy  
  
1.  W **Menu** edytora, wybierz polecenie menu.  
  
2.  W [okna właściwości](/visualstudio/ide/reference/properties-window), wpisz tekst na pasku stanu skojarzony w **monitu** pole.  
  

  
 **Wymagania**  
  
 MFC  
  
## <a name="see-also"></a>Zobacz też  
 [Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
 [Dodawanie poleceń do Menu](../windows/adding-commands-to-a-menu.md)   
 [Edytor menu](../windows/menu-editor.md)