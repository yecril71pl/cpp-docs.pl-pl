---
title: Tworzenie kontrolki ActiveX MFC
ms.date: 08/19/2019
f1_keywords:
- vc.appwiz.activex.project
helpviewer_keywords:
- MFC ActiveX controls [MFC], creating
- ActiveX controls [MFC], creating
ms.assetid: 8bd5a93c-d04d-414e-bb28-163fdc1c0dd5
ms.openlocfilehash: 19e9ca6f985423bb01a8dea38988c5dcf7285683
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91505964"
---
# <a name="creating-an-mfc-activex-control"></a>Tworzenie kontrolki ActiveX MFC

Programy sterujące ActiveX są programami modularnymi zaprojektowanymi w celu zapewnienia określonego typu funkcjonalności aplikacji nadrzędnej. Na przykład można utworzyć kontrolkę, taką jak przycisk do użycia w oknie dialogowym, lub pasek narzędzi do użycia na stronie sieci Web.

>[!IMPORTANT]
> Kontrolka ActiveX to Starsza technologia, która nie powinna być używana do nowych celów programistycznych. Aby uzyskać więcej informacji, zobacz [kontrolki ActiveX](../activex-controls.md).

Najprostszym sposobem tworzenia kontrolki ActiveX MFC jest użycie [Kreatora kontrolek ActiveX MFC](../../mfc/reference/mfc-activex-control-wizard.md).

### <a name="to-create-an-mfc-activex-control-using-the-mfc-activex-control-wizard"></a>Aby utworzyć formant ActiveX MFC przy użyciu kreatora kontrolki ActiveX MFC

1. Postępuj zgodnie z instrukcjami w temacie pomocy [Tworzenie aplikacji MFC,](creating-an-mfc-application.md) ale wybierz **formant ActiveX MFC** z listy dostępnych szablonów.

1. Zdefiniuj [Ustawienia aplikacji](../../mfc/reference/application-settings-mfc-activex-control-wizard.md), [nazwy kontrolek](../../mfc/reference/control-names-mfc-activex-control-wizard.md)i [Ustawienia kontrolki](../../mfc/reference/control-settings-mfc-activex-control-wizard.md) za pomocą Kreatora kontrolek ActiveX MFC.

    > [!NOTE]
    >  Pomiń ten krok, aby zachować ustawienia domyślne kreatora.

1. Kliknij przycisk **Zakończ** , aby zamknąć kreatora i otworzyć nowy projekt w środowisku programistycznym.

Po utworzeniu projektu można wyświetlić pliki utworzone w **Eksplorator rozwiązań**. Aby uzyskać więcej informacji na temat plików tworzonych przez kreatora dla projektu, zobacz plik wygenerowany przez projekt ReadMe.txt. Aby uzyskać więcej informacji na temat typów plików, zobacz [typy plików utworzonych dla projektów Visual Studio C++](../../build/reference/file-types-created-for-visual-cpp-projects.md).

Po utworzeniu projektu można użyć kreatorów kodu do dodawania [funkcji](../../ide/adding-a-member-function-visual-cpp.md#add-member-function-wizard), [zmiennych](../../ide/adding-a-member-variable-visual-cpp.md#add-member-variable-wizard), [zdarzeń](../../ide/adding-an-event-visual-cpp.md#add-event-wizard), [Właściwości](../../ide/adding-a-property-visual-cpp.md#names-add-property-wizard)i [metod](../../ide/adding-a-method-visual-cpp.md#add-method-wizard). Aby uzyskać więcej informacji na temat dostosowywania kontrolki ActiveX, zobacz [kontrolki ActiveX MFC](../../mfc/mfc-activex-controls.md).

## <a name="see-also"></a>Zobacz też

[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Strony właściwości](../../build/reference/property-pages-visual-cpp.md)
