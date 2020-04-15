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
ms.openlocfilehash: 6367b2a4b85b2c586c5a4420a8be1f80d334b2e4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363959"
---
# <a name="creating-an-mfc-dll-project"></a>Tworzenie projektu MFC DLL

Biblioteka DLL MFC to plik binarny, który działa jako biblioteka współużytkowana funkcji, które mogą być używane jednocześnie przez wiele aplikacji. Najprostszym sposobem utworzenia projektu biblioteki DLL MFC jest użycie Kreatora bibliotek dll MFC.

> [!NOTE]
> Wygląd funkcji w IDE może zależeć od aktywnych ustawień lub wersji i może różnić się od tych opisanych w Pomocy. Aby zmienić ustawienia, wybierz polecenie **Importuj i eksportuj ustawienia** w menu **Narzędzia.** Aby uzyskać więcej informacji, zobacz [Personalizowanie ide programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

### <a name="to-create-an-mfc-dll-project-using-the-mfc-dll-wizard"></a>Aby utworzyć projekt biblioteki DLL MFC przy użyciu Kreatora biblioteki DLL MFC

1. Postępuj zgodnie z instrukcjami w temacie pomocy [Tworzenie aplikacji MFC,](creating-an-mfc-application.md) ale wybierz **bibliotekę łącza dynamicznego MFC** lub **bibliotekę DLL MFC** z listy dostępnych szablonów.

1. Zdefiniuj ustawienia aplikacji za pomocą strony [ustawień aplikacji](../../mfc/reference/application-settings-mfc-dll-wizard.md) [Kreatora bibliotek DLL MFC](../../mfc/reference/mfc-dll-wizard.md).

    > [!NOTE]
    >  Pomiń ten krok, aby zachować domyślne ustawienia kreatora.

1. Kliknij **przycisk Zakończ,** aby zamknąć kreatora i otworzyć nowy projekt w **Eksploratorze rozwiązań**.

Po utworzeniu projektu można wyświetlić pliki utworzone w **Eksploratorze rozwiązań**. Aby uzyskać więcej informacji na temat plików, które kreator tworzy dla projektu, zobacz plik readme.txt generowany przez projekt. Aby uzyskać więcej informacji na temat typów plików, zobacz [Typy plików utworzone dla projektów programu Visual Studio C++](../../build/reference/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Zobacz też

[Typy projektów języka C++ w programie Visual Studio](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)<br/>
[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Strony właściwości](../../build/reference/property-pages-visual-cpp.md)
