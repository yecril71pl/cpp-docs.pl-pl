---
title: Dodawanie formantów do okna dialogowego spowoduje, że okno dialogowe przestaną działać | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], troubleshooting
- common controls, troubleshooting
- troubleshooting controls
- dialog boxes, troubleshooting
- dialog box controls, troubleshooting
- InitCommonControls
ms.assetid: b2dd4574-ea59-4343-8d65-b387cead5da6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b10c24955e74d08ab570b5b694628f42bb394268
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33858997"
---
# <a name="adding-controls-to-a-dialog-causes-the-dialog-to-no-longer-function"></a>Dodawanie formantów do okna dialogowego powodującego zatrzymanie działania okna dialogowego
Po dodaniu formantu wspólnego lub kontrolki zaawansowanej edycji do okna dialogowego, nie pojawi się podczas testowania okna dialogowego lub nie pojawi się okno dialogowe.  
  
 **Przykład problemu**  
  
1.  Utwórz projekt Win32, modyfikując ustawienia aplikacji, więc tworzenia aplikacji systemu Windows (nie aplikacji konsoli).  
  
2.  W [widok zasobów](../windows/resource-view-window.md), kliknij dwukrotnie plik .rc.  
  
3.  W obszarze opcji okna dialogowego, dwukrotnie kliknij **o** pola.  
  
4.  Dodaj **formant adresu IP** do okna dialogowego.  
  
5.  Zapisz i **odbudowanie wszystkiego**.  
  
6.  Wykonania programu.  
  
7.  W oknie dialogowym **pomocy** menu, kliknij przycisk **o** polecenia; nie okno dialogowe jest wyświetlane okno.  
  
 **Przyczyny**  
  
 Obecnie edytora okien dialogowych nie powoduje automatycznego dodania kodu do projektu podczas przeciągania i upuszczania następujące formanty standardowe lub edycji wzbogaconej formantów na okno dialogowe. Ani Visual Studio zapewnia błąd lub ostrzeżenie w przypadku wystąpienia tego problemu. Można ręcznie dodać kod dla formantu.  
  
||||  
|-|-|-|  
|Kontrolka suwaka|Formant drzewa|Wybór daty i godziny|  
|Pokrętła|Formantu karty|Kalendarza miesięcznego|  
|Formantu postępu|Formantu animacji|Formant adresu IP|  
|Klawisz dostępu|Kontrolka zaawansowanej edycji|Pole kombi rozszerzone|  
|Kontrolki listy|Formantu edycji wzbogaconej 2.0|Formant niestandardowy|  
  
## <a name="the-fix-for-common-controls"></a>Poprawka dla formantów standardowych  
 Aby można było używać formantów wspólnych w oknie dialogowym, należy wywołać [InitCommonControlsEx](http://msdn.microsoft.com/library/windows/desktop/bb775697) lub **AFXInitCommonControls** przed utworzeniem okna dialogowego.  
  
## <a name="the-fix-for-richedit-controls"></a>Poprawka dla formantów RichEdit  
 Należy wywołać **LoadLibrary** dla formantów edycji wzbogaconej. Aby uzyskać więcej informacji, zobacz [używanie formantu RichEdit 1.0 z MFC](../windows/using-the-richedit-1-0-control-with-mfc.md), [o zaawansowanej edycji kontrolki](http://msdn.microsoft.com/library/windows/desktop/bb787873) w [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)], i [Omówienie formantu edycji wzbogaconej](../mfc/overview-of-the-rich-edit-control.md).  
  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązywanie problemów z edytora okien dialogowych](../windows/troubleshooting-the-dialog-editor.md)   
 [Edytor okien dialogowych](../windows/dialog-editor.md)

