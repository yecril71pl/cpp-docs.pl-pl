---
title: Dodawanie obsługi zdarzeń dla formantów okna dialogowego (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Dialog Editor [C++], adding event handlers to controls
- controls [C++], event handlers
- dialog box controls [C++], events
- event handlers, for dialog box controls
ms.assetid: f9c70f24-ea6f-44df-82eb-78a2deaee769
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 156908a1611f8a1c8b22df61e6b789468753d25d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443088"
---
# <a name="adding-event-handlers-for-dialog-box-controls-c"></a>Dodawanie obsługi zdarzeń dla formantów okna dialogowego (C++)

Dla projektu oknach dialogowych, które są już skojarzone z klasą możesz korzystać z zalet niektóre skróty podczas tworzenia procedur obsługi zdarzeń. Można szybko utworzyć program obsługi zdarzenia powiadomień formantu domyślne lub wszystkie odpowiednie komunikaty Windows.

### <a name="to-create-a-handler-for-the-default-control-notification-event"></a>Aby utworzyć program obsługi zdarzenia powiadomień formantu domyślne

1. Kliknij dwukrotnie formant. **Tekstu** zostanie otwarty Edytor.

2. Dodaj kod procedury obsługi powiadamiania kontrolki w **tekstu** edytora.

### <a name="to-create-a-handler-for-any-applicable-windows-message"></a>Aby utworzyć procedury obsługi dla dowolnego odpowiednią wiadomość Windows

1. Kliknij formant, dla którego chcesz obsłużyć zdarzenie powiadomienia.

2. W [okno właściwości](/visualstudio/ide/reference/properties-window), kliknij przycisk **ControlEvents** przycisk, aby wyświetlić listę typowych zdarzeń Windows skojarzonego z kontrolką. Na przykład standardowy **OK** znajdujący się na **o** okno dialogowe wyświetla następujące zdarzenia powiadomień:

   - BN_CLICKED

   - BN_DOUBLECLICKED

   - BN_KILLFOCUS

   - BN_SETFOCUS

   > [!NOTE]
   > Alternatywnie, wybierz okno dialogowe i kliknij przycisk **ControlEvents** przycisk, aby wyświetlić listę typowych zdarzeń Windows dla wszystkich kontrolek w oknie dialogowym.

3. W **właściwości** okna, kliknij kolumnę prawym obok zdarzenia w celu obsługi, a następnie wybierz nazwę zdarzenia sugerowane powiadomień (na przykład `OnBnClickedOK` obsługuje BN_CLICKED).

   > [!NOTE]
   > Alternatywnie możesz podać nazwę procedury obsługi zdarzeń wybór, a nie wybrana domyślna nazwa programu obsługi zdarzeń.

   Po wybraniu zdarzenia programu Visual Studio otwiera **edytora tekstów** i wyświetla kod procedury obsługi zdarzeń. Na przykład, poniższy kod zostanie dodany do domyślnej `OnBnClickedOK`:

    ```cpp
    void CAboutDlg::OnBnClickedOk(void)
    {
        // TODO: Add your control notification handler code here
    }
    ```

Jeśli chcesz dodać program obsługi zdarzeń do klasy innej niż jedna implementacja okna dialogowego, użyj [Kreator obsługi zdarzeń](../ide/event-handler-wizard.md). Aby uzyskać więcej informacji, zobacz [Dodawanie obsługi zdarzeń](../ide/adding-an-event-handler-visual-cpp.md).

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Domyślne zdarzenia kontroli](../windows/default-control-events.md)<br/>
[Definiowanie zmiennych składowych dla kontrolek okna dialogowego](../windows/defining-member-variables-for-dialog-controls.md)<br/>
[Kontrolki okna dialogowego i typy zmiennych](../ide/dialog-box-controls-and-variable-types.md)<br/>
[Dodawanie klasy](../ide/adding-a-class-visual-cpp.md)<br/>
[Dodawanie funkcji członkowskiej](../ide/adding-a-member-function-visual-cpp.md)<br/>
[Dodawanie zmiennej członkowskiej](../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Zastępowanie funkcji wirtualnych](../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Handler komunikatów MFC](../mfc/reference/adding-an-mfc-message-handler.md)  