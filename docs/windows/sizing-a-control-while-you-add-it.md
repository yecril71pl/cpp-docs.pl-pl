---
title: Ustalanie rozmiaru formantu podczas dodawania go | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog box controls [C++], size
- controls [C++], sizing
ms.assetid: 06b1dd2b-0ba1-4e1f-adc3-cb73679f765e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e60803ec9696e541376aa8530cb4c01d32b9e569
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418865"
---
# <a name="sizing-a-control-while-you-add-it"></a>Ustalanie rozmiaru formantu podczas dodawania go

### <a name="to-size-a-control-while-you-add-it"></a>Rozmiar kontrolki podczas dodawania go

1. Wybierz kontrolkę w [okno przybornika](/visualstudio/ide/reference/toolbox).

2. Umieść kursor w miejscu (która jest wyświetlana jako krzyżowe na ekranie), w której chcesz lewego górnego rogu nowej kontrolki na Twoje okno dialogowe.

3. Kliknij i przytrzymaj naciśnięty przycisk myszy, aby móc zakotwiczyć w lewym górnym rogu formantu w oknie dialogowym, a następnie przeciągnij kursor w prawo i w dół, aż do uzyskania odpowiedni rozmiar kontrolki.

   > [!NOTE]
   > Faktycznie można zakotwiczyć dowolne dowiedzą o formant, który rysowania. Jako przykład tej procedurze użyto lewego górnego rogu.

4. Zwolnij przycisk myszy. Kontrolka jest gotowy do okna dialogowego w podany rozmiar.

   > [!TIP]
   > Można zmienić rozmiar formantu po upuszczenie na okno dialogowe, przenosząc uchwytów zmiany rozmiaru w obramowania formantu. Aby uzyskać więcej informacji, zobacz [ustalanie rozmiaru pojedynczych formantów](../windows/sizing-individual-controls.md).

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)<br/>
[Dodawanie obsługi zdarzeń dla kontrolek okna dialogowego](../windows/adding-event-handlers-for-dialog-box-controls.md)<br/>
[Kontrolki okna dialogowego i typy zmiennych](../ide/dialog-box-controls-and-variable-types.md)