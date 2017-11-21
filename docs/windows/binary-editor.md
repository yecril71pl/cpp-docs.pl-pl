---
title: "Edytor plików binarnych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.binary.F1
dev_langs: C++
helpviewer_keywords:
- editors, Binary
- resources [Visual Studio], editing
- resource editors, Binary editor
- Binary editor
ms.assetid: 2483c48b-1252-4dbc-826b-82e6c1a0e9cb
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cb758cfe3e454ad4448132da0216b1edd92941f8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](https://msdn.microsoft.com/library/f45fce5x.aspx) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](https://msdn.microsoft.com/library/xbx3z216.aspx). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
### <a name="requirements"></a>Wymagania  
 Brak  
  
## <a name="see-also"></a>Zobacz też  
 [Edytory zasobów](../windows/resource-editors.md)

