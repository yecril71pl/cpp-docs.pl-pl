---
title: 'Porady: otwieranie pliku skryptu zasobu spoza projektu (autonomicznego) | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.resource
dev_langs: C++
helpviewer_keywords:
- resources [Visual Studio], viewing
- rc files, viewing resources
- .rc files, viewing resources
- resource script files, viewing resources
ms.assetid: bc350c60-178d-4c5d-9a7e-6576b0c936e4
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cfe2df286960ca332a6c3d9ef33d53e0a5edb3bc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-open-a-resource-script-file-outside-of-a-project-standalone"></a>Porady: otwieranie pliku skryptu zasobu spoza projektu (autonomicznego)
Można wyświetlić zasobów w plik .rc, bez konieczności otwierania projektu. Plik .rc zostanie otwarty w oknie dokumentu w przeciwieństwie do otwierania w [widok zasobów](../windows/resource-view-window.md) okna (jak w przypadku plik jest otwarty w projekcie).  
  
> [!NOTE]
>  Jest to ważna różnica, ponieważ niektóre polecenia są dostępne tylko, gdy plik jest otwarty autonomiczny (spoza projektu). Na przykład można tylko zapisywania pliku w innym formacie lub inną nazwę pliku po otwarciu pliku spoza projektu ( **Zapisz jako** polecenie jest niedostępne, gdy plik jest otwarty w projekcie).  
  
### <a name="to-open-an-rc-file-outside-a-project"></a>Aby otworzyć plik .rc poza projektem  
  
1.  Z **pliku** menu, wybierz **Otwórz**, następnie kliknij przycisk **pliku**.  
  
2.  W **Otwórz plik** okna dialogowego Przejdź do pliku skryptu zasobu chcesz wyświetlić, zaznacz plik, a następnie kliknij pozycję **Otwórz**.  
  
    > [!NOTE]
    >  Jeśli Otwórz projekt (**pliku**, **Otwórz**, **projektu**), niektóre polecenia nie będą dostępne dla Ciebie. Otwierania pliku "autonomiczny" oznacza otwarcie go bez pierwszy ładowania projektu.  
  
 Aby otworzyć i wyświetlić plik zasobu w formacie tekstowym, zobacz [edycji skrypt zasobu (.rc) pliku](../windows/how-to-open-a-resource-script-file-in-text-format.md).  
  
#### <a name="to-open-multiple-rc-files-outside-a-project"></a>Do otwarcia wielu plików .rc poza projektem  
  
1.  Otwórz zarówno zasobów plików autonomicznych. Na przykład otwórz Source1.rc i Source2.rc.  
  
    1.  Z **pliku** menu, wybierz **Otwórz**, następnie kliknij przycisk **pliku**.  
  
    2.  W **Otwieranie pliku** okna dialogowego Przejdź do pierwszego pliku skryptu zasobu chcesz otworzyć (Source1.rc), zaznacz plik, a następnie kliknij pozycję **Otwórz**.  
  
    3.  Powtórz poprzedni krok, aby otworzyć drugiego pliku .rc (Source2.rc).  
  
         .RC — pliki są teraz otwarte w oddzielnych dokumentów w systemie windows.  
  
2.  Gdy zarówno .RC — pliki są otwarte, sąsiadująco, więc możesz przeglądać jednocześnie:  
  
    -   Z **okna** menu, wybierz **nową grupę kart poziomy** lub **nową grupę kart pionowy**.  
  
         \-lub -  
  
    -   Kliknij prawym przyciskiem myszy jeden z .RC — pliki i wybierz polecenie **nową grupę kart poziomy** lub **nową grupę kart pionowy** z menu skrótów.  
  
> [!NOTE]
>  Jeśli projekt nie zawiera już plik .rc, zobacz [Tworzenie nowego pliku skryptu zasobu](../windows/how-to-create-a-resource-script-file.md).  
  

  
### <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki zasobów](../windows/resource-files-visual-studio.md)   
 [Edytory zasobów](../windows/resource-editors.md)