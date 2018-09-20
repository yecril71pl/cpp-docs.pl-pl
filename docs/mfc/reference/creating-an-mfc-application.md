---
title: Tworzenie aplikacji MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- applications [MFC]
- MFC, creating applications
- MFC applications
ms.assetid: b8b8aa08-9c49-404c-8078-b42079ac18f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c20d3214f8f2f76fedaeebcd439f10e016ccdd9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410640"
---
# <a name="creating-an-mfc-application"></a>Tworzenie aplikacji MFC

Aplikacja MFC jest aplikacją wykonywalnego pliku dla Windows, który jest oparty na bibliotece Microsoft Foundation Class (MFC). Najprostszym sposobem utworzenia aplikacji MFC jest użycie Kreatora aplikacji MFC.

> [!IMPORTANT]
>  Projekty MFC nie są obsługiwane w wersjach programu Visual Studio Express.

Pliki wykonywalne MFC zazwyczaj należą do pięciu typów: standardowe aplikacje Windows, okna dialogowe, aplikacje oparte na formularzach, aplikacje w stylu Eksploratora i aplikacje w stylu przeglądarki sieci Web. Aby uzyskać więcej informacji, zobacz:

- [Używanie klas do pisania aplikacji Windows](../../mfc/using-the-classes-to-write-applications-for-windows.md)

- [Tworzenie i wyświetlanie okien dialogowych](../../mfc/creating-and-displaying-dialog-boxes.md)

- [Tworzenie aplikacji MFC opartej na formularzach](../../mfc/reference/creating-a-forms-based-mfc-application.md)

- [Tworzenie aplikacji MFC w stylu eksploratora plików](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)

- [Tworzenie aplikacji MFC w stylu przeglądarki internetowej](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)

Kreator aplikacji MFC generuje odpowiednie klasy i pliki dla dowolnego z tych typów aplikacji, w zależności od opcji wybranych w kreatorze.

### <a name="to-create-an-mfc-application-using-the-mfc-application-wizard"></a>Aby utworzyć aplikację MFC przy użyciu Kreatora aplikacji MFC

1. Postępuj zgodnie z instrukcjami w temacie Pomocy [Tworzenie projektu za pomocą Kreatora aplikacji Visual C++](../../ide/creating-desktop-projects-by-using-application-wizards.md).

1. W **nowy projekt** okno dialogowe, wybierz opcję **aplikacji MFC** w okienku szablonów, aby otworzyć kreatora.

1. Definiowanie ustawień aplikacji za pomocą [Kreator aplikacji MFC](../../mfc/reference/mfc-application-wizard.md).

    > [!NOTE]
    >  Pomiń ten krok, aby kreator ustawienia domyślne.

1. Kliknij przycisk **Zakończ** aby zamknąć kreatora i otworzyć nowy projekt w środowisku programistycznym.

Po utworzeniu projektu można przeglądać pliki utworzone w **Eksploratora rozwiązań**. Aby uzyskać więcej informacji o plikach Kreator tworzy dla projektu, zobacz plik ReadMe.txt wygenerowany przez projekt. Aby uzyskać więcej informacji na temat typów plików, zobacz [typy plików utworzonych dla projektów Visual C++](../../ide/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Zobacz też

[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Strony właściwości](../../ide/property-pages-visual-cpp.md)


