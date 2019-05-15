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
ms.openlocfilehash: cd1d7910d95fa7e412f9843da2cec7ae10a38ef6
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65708223"
---
# <a name="creating-an-mfc-dll-project"></a>Tworzenie projektu MFC DLL

Biblioteki MFC DLL jest plikiem binarnym, który działa jako współdzielona biblioteka funkcji, które mogą być używane jednocześnie przez wiele aplikacji. Najprostszym sposobem utworzenia projektu MFC DLL ma używać Kreatora MFC DLL.

> [!NOTE]
>  Wygląd funkcje w IDE może zależeć od ustawień aktywnych lub wersji i mogą się różnić od tych opisanych w Pomocy. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

### <a name="to-create-an-mfc-dll-project-using-the-mfc-dll-wizard"></a>Aby utworzyć projekt DLL MFC przy użyciu Kreatora MFC DLL

1. Postępuj zgodnie z instrukcjami w temacie Pomocy [Tworzenie projektu aplikacji konsoli w języku C++](../../get-started/tutorial-console-cpp.md).

**Uwaga** w **nowy projekt** okno dialogowe, wybierz opcję `MFC DLL` ikonę w okienku szablonów, aby otworzyć Kreatora MFC DLL.

1. Definiowanie ustawień aplikacji za pomocą [ustawienia aplikacji](../../mfc/reference/application-settings-mfc-dll-wizard.md) strony [kreatora MFC DLL](../../mfc/reference/mfc-dll-wizard.md).

    > [!NOTE]
    >  Pomiń ten krok, aby kreator ustawienia domyślne.

1. Kliknij przycisk **Zakończ** aby zamknąć kreatora i otworzyć nowy projekt w **Eksploratora rozwiązań**.

Po utworzeniu projektu można przeglądać pliki utworzone w **Eksploratora rozwiązań**. Aby uzyskać więcej informacji o plikach Kreator tworzy dla projektu, zobacz plik ReadMe.txt wygenerowany przez projekt. Aby uzyskać więcej informacji na temat typów plików, zobacz [typy plików utworzonych dla programu Visual Studio C++ projektów](../../build/reference/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Zobacz także

[C++typy projektów w programie Visual Studio](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)<br/>
[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Strony właściwości](../../build/reference/property-pages-visual-cpp.md)

