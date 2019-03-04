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
ms.openlocfilehash: 21173582f68b1d50fefbe22250546fcce63730b4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278837"
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

## <a name="see-also"></a>Zobacz także

[Typy projektów Visual C++](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)<br/>
[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Strony właściwości](../../ide/property-pages-visual-cpp.md)
