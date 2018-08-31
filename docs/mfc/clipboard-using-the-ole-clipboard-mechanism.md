---
title: 'Schowek: Korzystanie z mechanizmu Schowka OLE | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- applications [OLE], Clipboard
- OLE Clipboard
- Clipboard [MFC], OLE formats
- OLE Clipboard, formats
- formats [MFC], Clipboard for OLE
ms.assetid: 229cc610-5bb1-435e-bd20-2c8b9964d1af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d37618dccabd576a67c8b82a8b8ab38246254070
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43214708"
---
# <a name="clipboard-using-the-ole-clipboard-mechanism"></a>Schowek: korzystanie z mechanizmu schowka OLE
Do przesyłania danych do Schowka OLE używa standardowych formatów i niektóre formaty specyficzne dla OLE.  
  
 Gdy wycinanie i kopiowanie danych z aplikacji, dane są przechowywane w Schowku ma być używany w dalszej części operacji wklejania. Te dane są w różnych formatach. Jeśli użytkownik zdecyduje się na wklejanie danych ze Schowka, ją wybrać, które te formaty do użycia. Można zapisać aplikacji wybierz format, który zawiera większość informacji, chyba że użytkownik zaleci dla formatu przy użyciu Wklej specjalne. Przed kontynuowaniem, warto przeczytać [obiekty danych i źródeł danych (OLE)](../mfc/data-objects-and-data-sources-ole.md) tematów. Opisano podstawowe informacje dotyczące sposobu transfery danych w pracy i sposobie ich implementacji w aplikacjach.  
  
 Windows definiuje kilka standardowych formatów, które mogą służyć do przesyłania danych do Schowka. Obejmują one metapliki, tekst, mapy bitowe i inne. OLE definiuje liczbę OLE do formatów, jak również. W przypadku aplikacji wymagających więcej szczegółów niż podana przez tych formatów standardowych jest dobry pomysł, aby zarejestrować własne niestandardowe formaty Schowka. Użyj funkcji Win32 API [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) w tym celu.  
  
 Na przykład program Microsoft Excel rejestruje formatu niestandardowego dla arkuszy kalkulacyjnych. Ten format znacznie więcej informacji, niż na przykład niesie ze sobą, jest mapy bitowej. Gdy te dane są wklejane do aplikacji, która obsługuje formacie arkusza kalkulacyjnego, formuły i wartości z arkusza kalkulacyjnego są zachowywane i mogą być aktualizowane, jeśli to konieczne. Program Microsoft Excel również polega na spakowaniu danych ze Schowka w formatach tak, aby można było wkleić jako element OLE. Te informacje jako element osadzony wkleić dowolnego kontenera dokumentu OLE. Ten element osadzony można zmienić za pomocą programu Microsoft Excel. Schowek zawiera także proste mapy bitowej obrazu wybranego zakresu w arkuszu kalkulacyjnym. To również można wkleić do kontenery dokumentów OLE lub edytorów mapy bitowej, takich jak malowania. W przypadku mapy bitowej jednak nie ma możliwości można manipulować danymi jako arkusz kalkulacyjny.  
  
 Aby uzyskać maksymalną ilość danych ze Schowka, aplikacji powinna sprawdzać, czy te niestandardowe formaty przed wklejeniem danych ze Schowka.  
  
 Na przykład aby włączyć polecenie Cut, można napisać program obsługi podobny do poniższego:  
  
 [!code-cpp[NVC_MFCListView#3](../atl/reference/codesnippet/cpp/clipboard-using-the-ole-clipboard-mechanism_1.cpp)]  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat  
  
-   [Kopiowanie i wklejanie danych](../mfc/clipboard-copying-and-pasting-data.md)  
  
-   [Dodawanie innych formatów](../mfc/clipboard-adding-other-formats.md)  
  
-   [Korzystanie ze Schowka Windows](../mfc/clipboard-using-the-windows-clipboard.md)  
  
-   [OLE](../mfc/ole-background.md)  
  
-   [Źródła danych OLE obiekty i dane oraz jednolitego transferów danych](../mfc/data-objects-and-data-sources-ole.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Schowek](../mfc/clipboard.md)

