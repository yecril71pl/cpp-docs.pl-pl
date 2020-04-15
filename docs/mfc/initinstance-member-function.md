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
ms.openlocfilehash: 2cf5b266348e299fe761ba40bd2cfb849f02b9ab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377196"
---
# <a name="initinstance-member-function"></a>InitInstance — Funkcja członkowska

System operacyjny Windows umożliwia uruchomienie więcej niż jednej kopii lub "wystąpienia" tej samej aplikacji. `WinMain`wywołuje [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) za każdym razem, gdy uruchamia się nowe wystąpienie aplikacji.

Standardowa `InitInstance` implementacja utworzona przez Kreatora aplikacji MFC wykonuje następujące zadania:

- Jako akcję centralną tworzy szablony dokumentów, które z kolei tworzą dokumenty, widoki i okna ramek. Aby uzyskać opis tego procesu, zobacz [Tworzenie szablonu dokumentu](../mfc/document-template-creation.md).

- Ładuje standardowe opcje plików z pliku .ini lub rejestru systemu Windows, w tym nazwy ostatnio używanych plików.

- Rejestruje jeden lub więcej szablonów dokumentów.

- Dla aplikacji MDI tworzy okno ramki głównej.

- Przetwarza wiersz polecenia, aby otworzyć dokument określony w wierszu polecenia lub otworzyć nowy, pusty dokument.

Można dodać własny kod inicjowania lub zmodyfikować kod napisany przez kreatora.

> [!NOTE]
> Aplikacje MFC muszą być inicjowane jako jednowątkowy apartament (STA). Jeśli wywołasz [CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) w przesłonie, `InitInstance` określ COINIT_APARTMENTTHREADED (a nie COINIT_MULTITHREADED).

## <a name="see-also"></a>Zobacz też

[CWinApp: klasa aplikacji](../mfc/cwinapp-the-application-class.md)
