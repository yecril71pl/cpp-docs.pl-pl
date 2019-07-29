---
title: Tworzenie aplikacji MFC
ms.date: 07/28/2019
helpviewer_keywords:
- applications [MFC]
- MFC, creating applications
- MFC applications
ms.assetid: b8b8aa08-9c49-404c-8078-b42079ac18f0
ms.openlocfilehash: 454a994da6db2841317d41ea1cdacfd36b0705e4
ms.sourcegitcommit: 720b74dddb1cdf4e570d55103158304ee1df81f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/29/2019
ms.locfileid: "68606480"
---
# <a name="creating-an-mfc-application"></a>Tworzenie aplikacji MFC

Aplikacja MFC jest aplikacją wykonywalną dla systemu Windows opartą na bibliotece Microsoft Foundation Class (MFC). Najprostszym sposobem tworzenia aplikacji MFC jest użycie Kreatora aplikacji MFC (**projekt aplikacji MFC** w programie Visual Studio 2019). Aby utworzyć aplikację konsolową MFC, użyj Kreatora pulpitu systemu Windows, a następnie wybierz opcje **Aplikacja konsolowa** i **nagłówki MFC** .

> [!IMPORTANT]
>  Projekty MFC nie są obsługiwane w wersjach Visual Studio Express.

Pliki wykonywalne MFC zazwyczaj mieszczą się w pięciu typach: standardowe aplikacje systemu Windows, okna dialogowe, aplikacje oparte na formularzach, aplikacje w stylu Eksploratora i aplikacje w stylu przeglądarki sieci Web. Aby uzyskać więcej informacji, zobacz:

- [Korzystanie z klas do zapisywania aplikacji systemu Windows](../../mfc/using-the-classes-to-write-applications-for-windows.md)

- [Tworzenie i wyświetlanie okien dialogowych](../../mfc/creating-and-displaying-dialog-boxes.md)

- [Tworzenie aplikacji MFC opartej na formularzach](../../mfc/reference/creating-a-forms-based-mfc-application.md)

- [Tworzenie aplikacji MFC w stylu eksploratora plików](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)

- [Tworzenie aplikacji MFC w stylu przeglądarki internetowej](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)

Kreator aplikacji MFC generuje odpowiednie klasy i pliki dla dowolnego z tych typów aplikacji, w zależności od opcji wybranych w kreatorze.

### <a name="to-create-an-mfc-application-using-the-mfc-application-wizard"></a>Aby utworzyć aplikację MFC przy użyciu Kreatora aplikacji MFC

1. Postępuj zgodnie z instrukcjami w temacie pomocy [Tworzenie C++ projektu aplikacji konsoli](../../get-started/tutorial-console-cpp.md).

1. W oknie dialogowym **Nowy projekt** wybierz pozycję **aplikacja MFC** w okienku szablony, aby otworzyć kreatora.

1. Zdefiniuj ustawienia aplikacji za pomocą [Kreatora aplikacji MFC](../../mfc/reference/mfc-application-wizard.md).

    > [!NOTE]
    >  Pomiń ten krok, aby zachować ustawienia domyślne kreatora.

1. Kliknij przycisk **Zakończ** , aby zamknąć kreatora i otworzyć nowy projekt w środowisku programistycznym.

Po utworzeniu projektu można wyświetlić pliki utworzone w **Eksplorator rozwiązań**. Aby uzyskać więcej informacji na temat plików tworzonych przez kreatora dla projektu, zobacz plik Readme. txt wygenerowany przez projekt. Aby uzyskać więcej informacji na temat typów plików, zobacz [typy plików utworzonych dla projektów C++ programu Visual Studio](../../build/reference/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Zobacz także

[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Strony właściwości](../../build/reference/property-pages-visual-cpp.md)

