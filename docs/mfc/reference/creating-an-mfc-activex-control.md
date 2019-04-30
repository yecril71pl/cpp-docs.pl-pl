---
title: Tworzenie kontrolki ActiveX MFC
ms.date: 09/12/2018
f1_keywords:
- vc.appwiz.activex.project
helpviewer_keywords:
- MFC ActiveX controls [MFC], creating
- ActiveX controls [MFC], creating
ms.assetid: 8bd5a93c-d04d-414e-bb28-163fdc1c0dd5
ms.openlocfilehash: b2dc48e2568e180820f8bca008c66878af4b575e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372299"
---
# <a name="creating-an-mfc-activex-control"></a>Tworzenie kontrolki ActiveX MFC

Programy formantu ActiveX są moduły programy, w celu określonego typu funkcji do aplikacji nadrzędnej. Na przykład można utworzyć kontrolce, takiej jak przycisk do użycia w oknie dialogowym lub narzędzi do użycia na stronie sieci Web.

>[!IMPORTANT]
> ActiveX jest technologią starszą, która nie powinny być używane w przypadku nowych wdrożeń. Aby uzyskać więcej informacji, zobacz [formantów ActiveX](../activex-controls.md).

Najprostszym sposobem utworzenia kontrolki MFC ActiveX jest użycie [Kreator kontrolek ActiveX MFC](../../mfc/reference/mfc-activex-control-wizard.md).

### <a name="to-create-an-mfc-activex-control-using-the-mfc-activex-control-wizard"></a>Aby utworzyć formant ActiveX MFC przy użyciu Kreatora kontrolek ActiveX MFC

1. Postępuj zgodnie z instrukcjami w temacie Pomocy [Tworzenie projektu aplikacji konsoli w języku C++](../../get-started/tutorial-console-cpp.md).

1. W **nowy projekt** okno dialogowe, wybierz opcję **kontrolki ActiveX MFC** ikonę w okienku szablonów, aby otworzyć Kreator kontrolek ActiveX MFC.

1. Zdefiniuj swoje [ustawienia aplikacji](../../mfc/reference/application-settings-mfc-activex-control-wizard.md), [nazwy kontrolek](../../mfc/reference/control-names-mfc-activex-control-wizard.md), i [sterowanie ustawieniami](../../mfc/reference/control-settings-mfc-activex-control-wizard.md) przy użyciu Kreatora kontrolek ActiveX MFC.

    > [!NOTE]
    >  Pomiń ten krok, aby kreator ustawienia domyślne.

1. Kliknij przycisk **Zakończ** aby zamknąć kreatora i otworzyć nowy projekt w środowisku programistycznym.

Po utworzeniu projektu można przeglądać pliki utworzone w **Eksploratora rozwiązań**. Aby uzyskać więcej informacji o plikach Kreator tworzy dla projektu, zobacz plik ReadMe.txt wygenerowany przez projekt. Aby uzyskać więcej informacji na temat typów plików, zobacz [typy plików utworzonych dla projektów Visual C++](../../build/reference/file-types-created-for-visual-cpp-projects.md).

Po utworzeniu projektu umożliwia kreatorów kodu Dodaj [funkcje](../../ide/add-member-function-wizard.md), [zmienne](../../ide/add-member-variable-wizard.md), [zdarzenia](../../ide/add-event-wizard.md), [właściwości](../../ide/names-add-property-wizard.md), i [metody](../../ide/add-method-wizard.md). Aby uzyskać więcej informacji na temat dostosowywania formant ActiveX, zobacz [kontrolki ActiveX MFC](../../mfc/mfc-activex-controls.md).

## <a name="see-also"></a>Zobacz także

[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Strony właściwości](../../build/reference/property-pages-visual-cpp.md)

