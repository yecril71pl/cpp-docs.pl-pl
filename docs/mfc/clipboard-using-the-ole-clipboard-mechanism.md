---
title: 'Schowek: Korzystanie z mechanizmu Schowka OLE | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- applications [OLE], Clipboard
- OLE Clipboard
- Clipboard [MFC], OLE formats
- OLE Clipboard, formats
- formats [MFC], Clipboard for OLE
ms.assetid: 229cc610-5bb1-435e-bd20-2c8b9964d1af
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4996c6559ad20141fb84ed37e87fd1551e89a77b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="clipboard-using-the-ole-clipboard-mechanism"></a>Schowek: korzystanie z mechanizmu schowka OLE
OLE używa standardowych formatów i niektóre formaty OLE specyficzne dla transferu danych do Schowka.  
  
 Wycięte lub skopiować dane z aplikacji, dane są przechowywane w Schowku do użycia później w operacji wklejania. Te dane są w różnych formatach. Po wybraniu wklejanie danych ze Schowka, aplikacji można wybrać, które z tych formatów do użycia. Wybierz format, który zawiera większość informacji, chyba że użytkownik zaleci formatu przy użyciu Wklej specjalne mają być zapisywane aplikacji. Przed kontynuowaniem chcesz może odczytać [obiekty danych i źródła danych (OLE)](../mfc/data-objects-and-data-sources-ole.md) tematów. Opisano w nich podstawowe informacje dotyczące sposobu pracy transferu danych i sposobu ich wdrażania w aplikacji.  
  
 Windows definiuje kilka standardowych formatów, które mogą być używane do przesyłania danych do Schowka. Obejmują one metapliki, tekst, mapy bitowe i inne. OLE definiuje liczbę OLE formatów, jak również. Dla aplikacji, które wymagają więcej szczegółów niż podana przez te standardowych formatów zaleca się zarejestrować swoje własne niestandardowe formaty Schowka. Użyj funkcji Win32 API [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) w tym celu.  
  
 Na przykład program Microsoft Excel rejestruje formatu niestandardowego dla arkuszy kalkulacyjnych. Ten format niesie większej ilości informacji niż, na przykład, jest mapy bitowej. Gdy te dane mają być wklejone do aplikacji, która obsługuje formatu arkusza kalkulacyjnego, formuły i wartości z arkusza kalkulacyjnego są zachowywane i może zostać zaktualizowana w razie potrzeby. Program Microsoft Excel również umieszcza dane do Schowka w formatach tak, aby można było wkleić jako element OLE. Każdy kontener dokumentu OLE można wkleić te informacje jako element osadzony. Ten element osadzony można zmienić w programie Microsoft Excel. Schowek zawiera również proste mapy bitowej obrazu wybranego zakresu w arkuszu kalkulacyjnym. To również wkleić w kontenerach dokumentów OLE lub do edytora mapy bitowej, takich jak malowania. W przypadku mapy bitowej ponieważ nie ma można manipulować danymi jako arkusz kalkulacyjny.  
  
 Aby uzyskać maksymalną ilość informacji ze Schowka, aplikacje powinien sprawdzać istnienie te niestandardowe formaty przed wklejanie danych ze Schowka.  
  
 Na przykład aby włączyć polecenie Cut, można napisać obsługi postać zbliżoną do następującej:  
  
 [!code-cpp[NVC_MFCListView#3](../atl/reference/codesnippet/cpp/clipboard-using-the-ole-clipboard-mechanism_1.cpp)]  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Kopiowanie i wklejanie danych](../mfc/clipboard-copying-and-pasting-data.md)  
  
-   [Dodawanie innych formatów](../mfc/clipboard-adding-other-formats.md)  
  
-   [Korzystanie ze Schowka systemu Windows](../mfc/clipboard-using-the-windows-clipboard.md)  
  
-   [OLE](../mfc/ole-background.md)  
  
-   [Źródła danych OLE obiekty i dane oraz uniform transferów danych](../mfc/data-objects-and-data-sources-ole.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Schowek](../mfc/clipboard.md)

