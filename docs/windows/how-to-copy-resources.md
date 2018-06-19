---
title: 'Porady: Kopiowanie zasobów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.resvw.resource.copying
- vs.resvw.resource.copying
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio], moving between files
- resources [Visual Studio], copying
- resource files, copying or moving resources between
- resource files, tiling
- .rc files, copying resources between
- rc files, copying resources between
ms.assetid: 65f523e8-017f-4fc6-82d1-083c56d9131f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4b173be24e9f177a3156f740fcb07240c30fec75
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879851"
---
# <a name="how-to-copy-resources"></a>Porady: zasoby dotyczące kopiowania
Można skopiować zasobów z jednego pliku do innego bez konieczności ich zmieniania lub możesz [zmiana języka lub warunku zasobu podczas kopiowania go](../windows/how-to-change-the-language-or-condition-of-a-resource-while-copying.md).  
  
 Zasoby można łatwo kopiować z istniejącego zasobu lub plik wykonywalny do bieżącego pliku zasobu. Aby to zrobić, należy otworzyć oba pliki zawierające zasoby w tym samym czasie i przeciągnij elementy z jednego pliku lub skopiuj i Wklej między dwoma plikami. Ta metoda działa w przypadku plików zasobów skryptu (.rc) i pliki zasobów szablonu (.rct —), a także pliki wykonywalne (.exe).  
  
> [!NOTE]
>  Visual C++ zawiera przykładowe pliki zasobów, które można użyć w swojej aplikacji. Aby uzyskać więcej informacji, zobacz [CLIPART: wspólnych zasobów](http://msdn.microsoft.com/en-us/9bac2891-b6b3-49ec-a287-cec850c707e0).  
  
 Metoda przeciągania i upuszczania między .RC — pliki, które są otwarte [poza projektem](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).  
  
### <a name="to-copy-resources-between-files-using-the-drag-and-drop-method"></a>Aby umożliwić kopiowanie zasobów między plikami metodą przeciągnij i upuść  
  
1.  Otwórz zarówno autonomiczne pliki zasobów (Aby uzyskać więcej informacji, zobacz [wyświetlania zasobów w .rc z zewnątrz pliku projektu](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Na przykład otwórz Source1.rc i Source2.rc.  
  
2.  W pierwszym plik .rc kliknij zasób, do którego chcesz skopiować. Na przykład w Source1.rc, kliknij pozycję IDD_DIALOG1.  
  
3.  Naciśnij i przytrzymaj klawisz CTRL i przeciągnij go na drugi plik .rc. Na przykład przeciągnij IDD_DIALOG1 z Source1.rc Source2.rc.  
  
    > [!NOTE]
    >  Przeciąganie zasobu bez przytrzymując klawisz CTRL Przenosi zasób zamiast go kopiować.  
  
### <a name="to-copy-resources-using-copy-and-paste"></a>Do kopiowania zasobów za pomocą kopiowania i wklejania  
  
1.  Otwórz zarówno autonomiczne pliki zasobów (Aby uzyskać więcej informacji, zobacz [wyświetlania zasobów w .rc z zewnątrz pliku projektu](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Na przykład Source1.rc i Source2.rc.  
  
2.  W pliku źródłowym, z którego chcesz skopiować zasobów (na przykład Source1.rc), kliknij prawym przyciskiem myszy zasób, a następnie wybierz pozycję **kopiowania** z menu skrótów.  
  
3.  Kliknij prawym przyciskiem myszy plik zasobów, do którego chcesz wkleić zasobów (na przykład Source2.rc). Wybierz **Wklej** z menu skrótów.  
  
    > [!NOTE]
    >  Nie przeciągnij i upuść, skopiować, wycinanie lub wklejanie między pliki zasobów w projekcie (Widok zasobów) oraz .rc autonomicznej (te Otwórz w dokumencie systemu windows). Można to zrobić w poprzednich wersjach produktu.  
  
    > [!NOTE]
    >  W celu uniknięcia konfliktów z wartości w istniejącym pliku lub nazwy symbolu Visual C++ może zmienić zasobów przekazanych wartości symbolu lub nazwy symbolu oraz wartości podczas kopiowania do nowego pliku.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Wymagania  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: otwieranie pliku skryptu zasobu spoza projektu (autonomiczna)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)   
 [Pliki zasobów](../windows/resource-files-visual-studio.md)   
 [Edytory zasobów](../windows/resource-editors.md)