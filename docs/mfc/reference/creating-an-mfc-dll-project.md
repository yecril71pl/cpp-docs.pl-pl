---
title: Tworzenie projektu MFC DLL
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfcdll.project
helpviewer_keywords:
- MFC DLLs [MFC], creating projects
- DLLs [MFC], MFC
- projects [MFC], creating
- DLLs [MFC], creating
ms.assetid: 05540b93-4781-4a90-aadf-55158313f5b2
ms.openlocfilehash: 6a24fb136570d1b5984582cab3593a29d843a54c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50608120"
---
# <a name="creating-an-mfc-dll-project"></a>Tworzenie projektu MFC DLL

Biblioteki MFC DLL jest plikiem binarnym, który działa jako współdzielona biblioteka funkcji, które mogą być używane jednocześnie przez wiele aplikacji. Najprostszym sposobem utworzenia projektu MFC DLL ma używać Kreatora MFC DLL.

> [!NOTE]
>  Wygląd funkcje w IDE może zależeć od ustawień aktywnych lub wersji i mogą się różnić od tych opisanych w Pomocy. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

### <a name="to-create-an-mfc-dll-project-using-the-mfc-dll-wizard"></a>Aby utworzyć projekt DLL MFC przy użyciu Kreatora MFC DLL

1. Postępuj zgodnie z instrukcjami w temacie Pomocy [Tworzenie projektu za pomocą Kreatora aplikacji Visual C++](../../ide/creating-desktop-projects-by-using-application-wizards.md).

**Uwaga** w **nowy projekt** okno dialogowe, wybierz opcję `MFC DLL` ikonę w okienku szablonów, aby otworzyć Kreatora MFC DLL.

1. Definiowanie ustawień aplikacji za pomocą [ustawienia aplikacji](../../mfc/reference/application-settings-mfc-dll-wizard.md) strony [kreatora MFC DLL](../../mfc/reference/mfc-dll-wizard.md).

    > [!NOTE]
    >  Pomiń ten krok, aby kreator ustawienia domyślne.

1. Kliknij przycisk **Zakończ** aby zamknąć kreatora i otworzyć nowy projekt w **Eksploratora rozwiązań**.

Po utworzeniu projektu można przeglądać pliki utworzone w **Eksploratora rozwiązań**. Aby uzyskać więcej informacji o plikach Kreator tworzy dla projektu, zobacz plik ReadMe.txt wygenerowany przez projekt. Aby uzyskać więcej informacji na temat typów plików, zobacz [typy plików utworzonych dla projektów Visual C++](../../ide/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Zobacz też

[Typy projektów Visual C++](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)<br/>
[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Strony właściwości](../../ide/property-pages-visual-cpp.md)

