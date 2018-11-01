---
title: InitInstance — Funkcja członkowska
ms.date: 11/04/2016
f1_keywords:
- InitInstance
helpviewer_keywords:
- InitInstance method [MFC]
- applications [MFC], initializing
- MFC, initializing
- initializing MFC applications
ms.assetid: 4ef09267-ff7f-4c39-91a0-57454a264f83
ms.openlocfilehash: 6e430d30dc62a14008fad9e41e3b2cde7ddffc8b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50450599"
---
# <a name="initinstance-member-function"></a>InitInstance — Funkcja członkowska

System operacyjny Windows umożliwia uruchamianie więcej niż jedną kopię lub "wystąpienie" tej samej aplikacji. `WinMain` wywołania [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) za każdym razem, gdy uruchamia nowe wystąpienie aplikacji.

Standardowa `InitInstance` implementacji tworzone przez Kreatora aplikacji MFC wykonuje następujące zadania:

- Jako jej centralnej akcja tworzy szablonów dokumentów, które z kolei tworzyć dokumentów, widoków i okien ramowych. Aby uzyskać opis tego procesu, zobacz [Tworzenie szablonu dokumentu](../mfc/document-template-creation.md).

- Ładuje opcji standardowego pliku z pliku ini lub rejestru Windows, łącznie z nazwami ostatnio używanych plików.

- Rejestruje jedną lub więcej szablonów dokumentów.

- Aplikacja MDI tworzy się w oknie głównym ramki.

- Przetwarza wiersza polecenia, aby otworzyć dokument, określone w wierszu polecenia lub, aby otworzyć nowy pusty dokument.

Można dodawać kodu inicjowania lub modyfikować kod napisany przez kreatora.

> [!NOTE]
>  Aplikacji MFC muszą być zainicjowane w formacie komórek wielowątkowych pojedynczego (STA). Jeśli wywołasz [CoInitializeEx](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializeex) w swojej `InitInstance` zastąpienia, określ COINIT_APARTMENTTHREADED (zamiast COINIT_MULTITHREADED).

## <a name="see-also"></a>Zobacz też

[CWinApp: klasa aplikacji](../mfc/cwinapp-the-application-class.md)
