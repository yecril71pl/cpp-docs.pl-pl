---
title: Zaznaczanie obszaru obrazu (edytor obrazów dla ikon) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.image.editing
dev_langs:
- C++
helpviewer_keywords:
- Image editor [C++], image selection
- Image editor [C++], selecting images
- images [C++], selecting
- cursors [C++], selecting areas of
ms.assetid: 8b6ce4ad-eba1-4ece-86ba-cea92c3edff2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 07cb7528e25604e873f6da92193a97cf79700799
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890119"
---
# <a name="selecting-an-area-of-an-image-image-editor-for-icons"></a>Zaznaczanie obszaru obrazu (Edytor obrazów dla ikon)
Narzędzia wyboru umożliwia definiowanie obszar obrazu, który ma wycinanie, kopiowanie, wyczyść, rozmiar, Odwróć lub przenieść. Z **prostokąta zaznaczenia** narzędzia można zdefiniować i wybierz prostokątny obszar obrazu. Z **nieregularne wybór** narzędzia można narysować odręcznej konspektu obszaru chcesz wybrać wycinania, kopiowania lub innej operacji.  
  
> [!NOTE]
>  Zobacz **prostokąta zaznaczenia** i **nieregularne wybór** narzędzia przedstawianych w [paska narzędzi edytora obrazów](../windows/toolbar-image-editor-for-icons.md) lub wyświetlanie podpowiedzi skojarzone z każdym przycisku na **Edytor obrazów** paska narzędzi.  
  
 Można również utworzyć pędzla niestandardowego z zaznaczenia. Aby uzyskać więcej informacji, zobacz [Tworzenie pędzla niestandardowego](../windows/creating-a-custom-brush-image-editor-for-icons.md).  
  
### <a name="to-select-an-area-of-an-image"></a>Aby wybrać obszar obrazu  
  
1.  Na **edytor obrazów** paska narzędzi (lub z **obrazu** menu **narzędzia** polecenia), kliknij przycisk Narzędzie wyboru mają.  
  
2.  Przenieś punkt wstawiania do jednego rogu obszaru obrazu, który chcesz wybrać. Na ekranie są wyświetlane, gdy punkt wstawiania znajduje się nad obrazu.  
  
3.  Przeciągnij punkt wstawiania przeciwną rogu obszaru, który chcesz wybrać. Prostokąt pokazuje, które piksele zostanie wybrany. Wszystkie piksele w prostokącie, włącznie z zawartymi w obszarze prostokąta, znajdują się w zaznaczeniu.  
  
4.  Zwolnij przycisk myszy. Obramowanie wyboru umieszcza obszaru.  
  
### <a name="to-select-an-entire-image"></a>Aby wybrać całego obrazu  
  
1.  Kliknij obraz poza bieżącym zaznaczeniu. Obramowanie wyboru zmiany fokusu i ponownie obejmuje całego obrazu.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Wymagania  
  
 Brak  
  
## <a name="see-also"></a>Zobacz też  
 [Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Edytowanie zasobów graficznych](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)

