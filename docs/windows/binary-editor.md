---
title: "Edytor plików binarnych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.editors.binary.F1
dev_langs:
- C++
helpviewer_keywords:
- editors, Binary
- resources [Visual Studio], editing
- resource editors, Binary editor
- Binary editor
ms.assetid: 2483c48b-1252-4dbc-826b-82e6c1a0e9cb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4dade674fb32615e23904e6dbaf03d6c6ee0a371
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="binary-editor"></a>Edytor plików binarnych
> [!WARNING]
>  Edytor plików binarnych nie jest dostępna w wersji Express.  
  
 Edytor plików binarnych umożliwia edytowanie wszystkich zasobów na poziomie binarnym w formacie szesnastkowym lub w formacie ASCII. Można również użyć [znaleźć polecenia](/visualstudio/ide/reference/find-command) do wyszukiwania ciągów znaków ASCII lub bajty szesnastkowe. Edytor plików binarnych należy używać tylko wtedy, gdy należy wyświetlić lub drobne zmiany niestandardowych zasobów lub typy zasobów, które nie są obsługiwane przez środowisko Visual Studio.  
  
 Aby otworzyć edytora plików binarnych, należy najpierw wybrać **plik &#124; Nowy &#124; Plik** z menu głównego, wybierz plik, który chcesz edytować, a następnie kliknij strzałkę listy obok **Otwórz** przycisk, a następnie wybierz pozycję **Otwórz za pomocą &#124; Edytor plików binarnych**.  
  
> [!CAUTION]
>  Edytowanie zasobów, takich jak okien dialogowych, obrazy lub menu w edytorze binarnym jest niebezpieczne. Niepoprawne edytowanie może spowodować uszkodzenie zasobów, dzięki czemu można odczytać w edytorze macierzystego.  
  
> [!TIP]
>  Podczas używania Edytor plików binarnych w wielu przypadkach, należy kliknąć prawym przyciskiem myszy do wyświetlenia menu skrótów poleceń określonych zasobów. Dostępne polecenia zależą od tego, co Twoje kursor do. Na przykład jeśli klikniesz przycisk podczas wskazujący Edytor plików binarnych z wybranych wartości szesnastkowych, pokazuje menu skrótów **Wytnij**, **kopiowania**, i **Wklej** poleceń.  
  
 Edytor plików binarnych można:  
  
-   [Otwieranie zasobów do edycji plików binarnych](../windows/opening-a-resource-for-binary-editing.md)  
  
-   [Edytowanie danych binarnych](../windows/editing-binary-data.md)  
  
-   [Znajdowanie danych binarnych](../windows/finding-binary-data.md)  
  
-   [Utwórz nowy zasób niestandardowy lub danych](../windows/creating-a-new-custom-or-data-resource.md)  
  
## <a name="managed-resources"></a>Zarządzane zasoby  
 Można użyć [edytor obrazów](../windows/image-editor-for-icons.md) i Edytor plików binarnych do pracy z plikami zasobów w projektach zarządzanych. Wszelkie zarządzane zasoby, które chcesz edytować, muszą być powiązanymi zasobami. Edytory zasobów programu Visual Studio nie obsługują edycji zasobów osadzonych.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
### <a name="requirements"></a>Wymagania  
 Brak  
  
## <a name="see-also"></a>Zobacz też  
 [Edytory zasobów](../windows/resource-editors.md)

