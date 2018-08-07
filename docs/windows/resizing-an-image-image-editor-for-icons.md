---
title: Zmiana rozmiaru obrazu (edytor obrazów dla ikon) | Dokumentacja firmy Microsoft
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
- Image editor [C++], resizing images
- graphics [C++], resizing
- images [C++], resizing
- resizing images
ms.assetid: d83a02c4-4dfe-4586-a0df-51a50c2ba71d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 41494e8b88f41c4c842e95e9f8a9f5da0247739f
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39605646"
---
# <a name="resizing-an-image-image-editor-for-icons"></a>Zmiana rozmiaru obrazu (Edytor obrazów dla ikon)
Zachowanie edytora obrazów podczas zmiany rozmiaru obrazu zależy od tego, czy masz [wybranego](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md) całego obrazu lub jego część.  
  
 Zaznaczenie zawiera tylko część obrazu, edytora obrazów zmniejsza zaznaczenie przez usunięcie wierszy lub kolumn pikseli i wypełniania opuszczonych regionów z bieżącym kolorem tła lub rozciąga zaznaczenie zduplikowane wiersze lub kolumny w pikselach.  
  
 Jeśli zaznaczenie obejmuje cały obraz, edytora obrazów albo zmniejsza rozciąga obrazu, lub przycina i rozszerza je.  
  
 Istnieją dwa mechanizmy do zmiany rozmiaru obrazu: uchwytów zmiany rozmiaru i [okno właściwości](/visualstudio/ide/reference/properties-window). Można przeciągnąć uchwyty zmiany rozmiaru, aby zmienić rozmiar wszystkich lub część obrazu. Uchwyty zmiany rozmiaru, które można przeciągać są wypełnione. Nie można przeciągnąć uchwyty, które są puste. Można użyć okna właściwości zmiana rozmiaru całego obrazu tylko wybranej części.  
  
 ![Uchwytów na mapę bitową](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")  
Uchwyty zmiany rozmiaru  
  
> [!NOTE]
>  W przypadku kafelka siatki opcji wybranej w [okno dialogowe Ustawienia siatki](../windows/grid-settings-dialog-box-image-editor-for-icons.md), następnie zmiany rozmiaru przyciąganie do następnego wiersza siatki kafelka. Siatka pikseli, opcja jest zaznaczona (ustawienie domyślne), jeśli tylko zmiany rozmiaru przyciąganie do następnego dostępne pikseli.  
  
-   [Zmiana rozmiaru całego obrazu](../windows/resizing-an-entire-image-image-editor-for-icons.md)  
  
-   [Przycinanie i rozszerzanie całego obrazu](cropping-or-extending-an-entire-image-image-editor-for-icons.md)  
  
-   [Zmniejszanie i rozciąganie całego obrazu](../windows/shrinking-or-stretching-an-entire-image-image-editor-for-icons.md)  
  
-   [Zmniejszanie i rozciąganie części obrazu](../windows/shrinking-or-stretching-part-of-an-image-image-editor-for-icons.md)  
  
 Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Wymagania  
 Brak  
  
## <a name="see-also"></a>Zobacz też  
 [Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Edytowanie zasobów graficznych](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)