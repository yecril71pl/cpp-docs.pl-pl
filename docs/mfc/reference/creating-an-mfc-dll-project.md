---
title: Tworzenie projektu MFC DLL
ms.date: 08/19/2019
f1_keywords:
- vc.appwiz.mfcdll.project
helpviewer_keywords:
- MFC DLLs [MFC], creating projects
- DLLs [MFC], MFC
- projects [MFC], creating
- DLLs [MFC], creating
ms.assetid: 05540b93-4781-4a90-aadf-55158313f5b2
ms.openlocfilehash: 649a47abea23aedb9aa97bb4923e7a800348e27e
ms.sourcegitcommit: bf1940a39029dbbd861f95480f55e5e8bd25cda0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70108479"
---
# <a name="creating-an-mfc-dll-project"></a>Tworzenie projektu MFC DLL

Biblioteka MFC DLL to plik binarny, który działa jako udostępniona biblioteka funkcji, które mogą być używane jednocześnie przez wiele aplikacji. Najprostszym sposobem tworzenia projektu MFC DLL jest użycie kreatora MFC DLL.

> [!NOTE]
>  Wygląd funkcji w IDE może zależeć od ustawień aktywnych lub wydania i może się różnić od tych opisanych w pomocy. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

### <a name="to-create-an-mfc-dll-project-using-the-mfc-dll-wizard"></a>Aby utworzyć projekt MFC DLL przy użyciu kreatora MFC DLL

1. Postępuj zgodnie z instrukcjami podanymi w temacie dotyczącym [tworzenia aplikacji MFC](creating-an-mfc-application.md) , ale z listy dostępnych szablonów wybierz opcję **biblioteka dołączana dynamicznie MFC** lub biblioteka **MFC DLL** .

1. Zdefiniuj ustawienia aplikacji, korzystając ze strony [Ustawienia aplikacji](../../mfc/reference/application-settings-mfc-dll-wizard.md) [kreatora MFC DLL](../../mfc/reference/mfc-dll-wizard.md).

    > [!NOTE]
    >  Pomiń ten krok, aby zachować ustawienia domyślne kreatora.

1. Kliknij przycisk **Zakończ** , aby zamknąć kreatora i otworzyć nowy projekt w **Eksplorator rozwiązań**.

Po utworzeniu projektu można wyświetlić pliki utworzone w **Eksplorator rozwiązań**. Aby uzyskać więcej informacji na temat plików tworzonych przez kreatora dla projektu, zobacz plik Readme. txt wygenerowany przez projekt. Aby uzyskać więcej informacji na temat typów plików, zobacz [typy plików utworzonych dla projektów C++ programu Visual Studio](../../build/reference/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Zobacz także

[C++typy projektów w programie Visual Studio](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)<br/>
[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Strony właściwości](../../build/reference/property-pages-visual-cpp.md)

