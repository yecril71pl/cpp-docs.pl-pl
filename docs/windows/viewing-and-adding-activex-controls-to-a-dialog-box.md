---
title: Wyświetlanie i dodawanie kontrolek ActiveX do okna dialogowego (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.controls.activex
helpviewer_keywords:
- dialog boxes [C++], adding ActiveX controls
- ActiveX controls [C++], adding to dialog boxes
ms.assetid: e1c2e3ae-e1b0-40d3-9766-623007073856
ms.openlocfilehash: 947318fb9f628c1184398c039c9697128b09c869
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642510"
---
# <a name="viewing-and-adding-activex-controls-to-a-dialog-box-c"></a>Wyświetlanie i dodawanie kontrolek ActiveX do okna dialogowego (C++)

Program Visual Studio umożliwia wstawianie kontrolki ActiveX z okna dialogowego.

### <a name="to-see-the-activex-controls-you-have-available"></a>Aby wyświetlić kontrolki ActiveX masz dostępne

1. Otwórz okno dialogowe, w edytorze okien dialogowych.

2. Kliknij prawym przyciskiem myszy kliknij w dowolnym miejscu w treści okno dialogowe.

3. W menu skrótów kliknij **Wstawianie formantu ActiveX**.

   [Wstawianie formantu ActiveX, okno dialogowe](../windows/insert-activex-control-dialog-box.md) wyświetlona kontrolek ActiveX w Twoim systemie. W dolnej części okna dialogowego jest wyświetlana ścieżka do pliku formantu ActiveX.

### <a name="to-add-an-activex-control-to-a-dialog-box"></a>Aby dodać formant ActiveX do okna dialogowego

1. W [Wstawianie formantu ActiveX, okno dialogowe](../windows/insert-activex-control-dialog-box.md), wybierz kontrolkę chcesz dodać do swojej okno dialogowe, a następnie kliknij przycisk **OK**.

   Formant ma być wyświetlany w oknie dialogowym, w którym można go edytować lub tworzyć programy obsługi dla niego tak samo, jak dowolną inną kontrolką.

   > [!NOTE]
   > Można dodać formanty ActiveX do [okno przybornika](/visualstudio/ide/reference/toolbox).

   > [!CAUTION]
   > Może nie być prawne rozpowszechnianie wszystkich kontrolek ActiveX w Twoim systemie. Zapoznaj się z umową licencyjną dotyczącą oprogramowania, zainstalowanego kontrolki lub skontaktuj się z firmą oprogramowania.

   Możesz umieścić formantów w **przybornika** okna, aby mieć łatwy dostęp. Aby uzyskać więcej informacji, zobacz [przybornika](/visualstudio/ide/reference/toolbox).

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)<br/>
[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Kontenery kontrolek ActiveX](../mfc/activex-control-containers.md)