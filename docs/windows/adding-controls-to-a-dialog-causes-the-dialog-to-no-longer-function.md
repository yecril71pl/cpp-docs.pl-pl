---
title: Dodawanie formantów do okna dialogowego powoduje, że okno dialogowe przestaną działać | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 6d27c12b491fc5f05da58a84703ea13e84e9e9c6
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43215373"
---
# <a name="adding-controls-to-a-dialog-causes-the-dialog-to-no-longer-function"></a>Dodawanie formantów do okna dialogowego powodującego zatrzymanie działania okna dialogowego

Po dodaniu wspólne kontrolki lub kontrolki edycji wzbogaconej w oknie dialogowym, nie pojawi się podczas testowania okna dialogowego lub nie pojawi się okno dialogowe.

### <a name="example-of-the-problem"></a>Przykład problemu

1. Utwórz projekt systemu Win32, modyfikując ustawienia aplikacji, dzięki czemu można utworzyć aplikację Windows (nie Aplikacja konsoli).

2. W [widok zasobów](../windows/resource-view-window.md), kliknij dwukrotnie plik .rc.

3. Kliknij dwukrotnie w ramach opcji okna dialogowego **o** pole.

4. Dodaj **formant adresu IP** do okna dialogowego.

5. Zapisz i **ponowna kompilacja**.

6. Wykonywanie programu.

7. W oknie dialogowym **pomocy** menu, kliknij przycisk **o** polecenia; nie okno dialogowe zostanie wyświetlone okno.

### <a name="the-cause"></a>Przyczyny

Obecnie Edytor okien dialogowych nie powoduje automatycznego dodania kodu do projektu podczas przeciągania i upuszczania następujące formanty standardowe lub formanty edycji wzbogaconej na okno dialogowe. Ani Visual Studio zapewnia błąd lub ostrzeżenie w przypadku wystąpienia tego problemu. Można ręcznie dodać kodu dla formantu.

||||
|-|-|-|
|Kontrolka suwaka|Kontrolka drzewa|Wybór daty i godziny|
|Kontrolki pokrętła|Kontrolki karty|Kalendarza miesięcznego|
|Kontrolki postępu|Kontrolki animacji|Formant adresu IP|
|Klawisz skrótu|Formantu edycji wzbogaconej|Pole kombi rozszerzone|
|Kontrolka listy|Formantu edycji wzbogaconej w wersji 2.0|Kontrolka niestandardowa|

## <a name="the-fix-for-common-controls"></a>Poprawka dla formantów standardowych

Aby można było używać wspólnych formantów w oknie dialogowym, należy wywołać [InitCommonControlsEx](/windows/desktop/api/commctrl/nf-commctrl-initcommoncontrolsex) lub `AFXInitCommonControls` przed utworzeniem okna dialogowego.

## <a name="the-fix-for-richedit-controls"></a>Poprawka dla kontrolki RichEdit

Należy wywołać `LoadLibrary` dla formantów edycji. Aby uzyskać więcej informacji, zobacz [używanie formantu RichEdit 1.0 z MFC](../windows/using-the-richedit-1-0-control-with-mfc.md), [o Zaawansowane formanty edycji](/windows/desktop/Controls/about-rich-edit-controls) w zestawie Windows SDK i [Omówienie formantu edycji rozbudowane](../mfc/overview-of-the-rich-edit-control.md).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Rozwiązywanie problemów z Edytorem okien dialogowych](../windows/troubleshooting-the-dialog-editor.md)  
[Edytor okien dialogowych](../windows/dialog-editor.md)