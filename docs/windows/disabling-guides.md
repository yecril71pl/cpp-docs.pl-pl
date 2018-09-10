---
title: Wyłączanie prowadnic | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- guides, disabling snapping
- Dialog editor [C++], snap to guides
- snap to guides (Dialog editor)
- controls [C++], snap to guides/grid
ms.assetid: 51efa07b-8684-474e-a0b4-191ec5d91d1a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1e3ae2e982ce04743644f9c94d9c163478c0b67e
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313120"
---
# <a name="disabling-guides"></a>Wyłączanie prowadnic

Klawisze specjalne w połączeniu z myszy umożliwia wyłączanie przyciągania efekt prowadnice. Za pomocą **Alt** klucz wyłącza przyciągania skutki przewodnik wybrane. Przenoszenie Przewodnik z **Shift** klucz uniemożliwia przyciągniętą posuwał się z przewodnikiem.

### <a name="to-disable-the-snapping-effect-of-the-guides"></a>Aby wyłączyć przyciąganie efekt prowadnice

1. Przeciągnij formant, przytrzymując naciśnięty **Alt** klucza.

### <a name="to-move-guides-without-moving-the-snapped-controls"></a>Aby przenieść przewodniki bez przenoszenia przyciągniętą

1. Przeciągnij przewodnika, przytrzymując naciśnięty **Shift** klucza.

### <a name="to-turn-off-the-guides"></a>Aby wyłączyć prowadnice

1. Z **Format** menu, wybierz **ustawienia prowadnic**.

2. W [okno dialogowe Ustawienia prowadnic](../windows/guide-settings-dialog-box.md)w obszarze **prowadnic układu**, wybierz opcję **Brak**.

   > [!NOTE]
   > Możesz także dwukrotnie kliknąć na pasku linijkę, aby uzyskać dostęp do **ustawienia prowadnic** okno dialogowe.

\- lub —

- Na **Format** menu, kliknij przycisk **Przełącz prowadnice**.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Stany dla Edytora okien dialogowych (prowadnice i siatki)](../windows/dialog-editor-states-guides-and-grids.md)  
[Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)