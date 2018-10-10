---
title: InitInstance, Skladowa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- InitInstance
dev_langs:
- C++
helpviewer_keywords:
- InitInstance method [MFC]
- applications [MFC], initializing
- MFC, initializing
- initializing MFC applications
ms.assetid: 4ef09267-ff7f-4c39-91a0-57454a264f83
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bc9d1d1ff35755a966591e6f46f7742ddfa59e08
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890026"
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
