---
title: Tworzenie ikony 256 kolorów (edytor obrazów dla ikon) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- 256-color palette
- cursors, color
- colors, icons
- colors, cursors
- icons, color
ms.assetid: 2738089b-4fd3-4c45-96ae-6a15e4c6b780
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 34336a62574e83a25af5341c753df78be72a6a15
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601686"
---
# <a name="creating-a-256-color-icon-or-cursor-image-editor-for-icons"></a>Tworzenie ikony 256 kolorów (Edytor obrazów dla ikon)

Za pomocą **obraz** edytora, ikon i kursorów można wielkości dużych (64 × 64) z palety 256 kolorów do wyboru. Po utworzeniu zasobu stylu obrazu urządzenia jest zaznaczone.

### <a name="to-create-a-256-color-icon-or-cursor"></a>Tworzenie ikony 256 kolorów lub kursora

1. W [widok zasobów](../windows/resource-view-window.md), kliknij prawym przyciskiem myszy plik .rc, a następnie wybierz **Wstaw zasobów** z menu skrótów. (Jeśli masz już istniejący zasób obrazu w pliku .rc, takich jak kursora, użytkownik może po prostu kliknij prawym przyciskiem myszy **kursora** i wybierz polecenie **wstawiania kursora** z menu skrótów.)

   > [!NOTE] 
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

2. W [Wstaw zasób — okno dialogowe](../windows/add-resource-dialog-box.md), wybierz opcję **ikonę** lub **kursora** i kliknij przycisk **New**.

3. Na **obraz** menu, kliknij przycisk **nowy obraz urządzenia**.

4. Wybierz żądany styl obrazu 256 kolorów.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Korzystanie z palety 256 kolorów](../windows/using-the-256-color-palette-image-editor-for-icons.md)  
[Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)  
[Ikony i kursory: zasoby obrazów do wyświetlania na urządzeniach](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)