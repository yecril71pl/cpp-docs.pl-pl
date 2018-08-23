---
title: Wyświetlanie i dodawanie kontrolek ActiveX do okna dialogowego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.controls.activex
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [C++], adding ActiveX controls
- Insert ActiveX Control command
- ActiveX controls [C++], adding to dialog boxes
ms.assetid: e1c2e3ae-e1b0-40d3-9766-623007073856
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 95dbd8003f95ee0c0e809d9017ec5093b782ae99
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604664"
---
# <a name="viewing-and-adding-activex-controls-to-a-dialog-box"></a>Wyświetlanie i dodawanie kontrolek ActiveX do okna dialogowego

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
   > Można dodać formanty ActiveX do [okno przybornika](/visualstudio/ide/reference/toolbox). Aby uzyskać więcej informacji, zobacz [elementów zarządzania i karty w przyborniku](http://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).

   > [!CAUTION]
   > Może nie być prawne rozpowszechnianie wszystkich kontrolek ActiveX w Twoim systemie. Zapoznaj się z umową licencyjną dotyczącą oprogramowania, zainstalowanego kontrolki lub skontaktuj się z firmą oprogramowania.

   Możesz umieścić formantów w **przybornika** okna, aby mieć łatwy dostęp. Aby uzyskać więcej informacji, zobacz [dostosowywania przybornika, okno dialogowe](http://msdn.microsoft.com/bd07835f-18a8-433e-bccc-7141f65263bb).

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)  
[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)  
[Kontenery kontrolek ActiveX](../mfc/activex-control-containers.md)