---
title: Zaznaczanie kontrolek | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Dialog editor, selecting controls
- dominant controls
- dialog box controls, selecting in editor
- controls [C++], selecting
- size, controls
- controls [C++], dominant
ms.assetid: 27f05450-4550-4229-9f4c-2c9e06365596
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5517695da652dfd1eaa34b6ffd68fa90eac1a397
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40012872"
---
# <a name="selecting-controls"></a>Zaznaczanie kontrolek
Wybierać formanty do rozmiaru, wyrównanie, przenieść, skopiować, lub je usunąć, a następnie wykonaj operację, którą chcesz. W większości przypadków należy wybrać więcej niż jeden formant na korzystanie z narzędzia określania rozmiaru i wyrównanie [paska narzędzi edytora okien dialogowych](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).  
  
 Po wybraniu formantu, ma przyciemnione obramowanie wokół niej z niezawodnej (aktywny) lub pusty (nieaktywny) "uchwytów," małe kwadraty, są wyświetlane w krawędź zaznaczenia. Po wybraniu wielu formantów formantu dominującego ma uchwyty zmiany rozmiaru solid; wszystkie inne wybrane formanty mają uchwyty zmiany rozmiaru pusty.  
  
 Podczas zmiany rozmiaru lub wyrównywanie formantów wielu **okna dialogowego** Edytor używa "formantu dominującego" Aby określić, jak rozmiar lub wyrównane do innych kontrolek. Domyślnie formant dominujący jest pierwszy formant wybrane.  
  
-   [Wybieranie wielu kontrolek](../windows/selecting-multiple-controls.md)  
  
-   [Określanie kontrolki dominującej](../windows/specifying-the-dominant-control.md)  
  
 Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Formanty w oknach dialogowych](../windows/controls-in-dialog-boxes.md)   
 [Kontrolki](../mfc/controls-mfc.md)