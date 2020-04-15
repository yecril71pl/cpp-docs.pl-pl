---
title: Współpraca z udostępnianiem na żywo dla języka C++ w programie Visual Studio
description: Użyj udostępniania na żywo dla języka C++ w programie Visual Studio do współpracy i udostępniania kodu w czasie rzeczywistym.
ms.date: 05/24/2019
ms.openlocfilehash: 0ebdd77d0e277778b48cf69024b24841f775d968
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377284"
---
# <a name="collaborate-using-live-share-for-c"></a>Współpraca przy użyciu rozszerzenia Live Share dla języka C++

W programie Visual Studio 2019 i visual studio code można używać **udostępniania na żywo** do współpracy nad projektami języka C++ w czasie rzeczywistym. Za **pomocą funkcji Live Share** inna osoba może edytować i debugować kod bez konieczności instalowania projektu lub jego zależności. Zmiany są widoczne w miarę ich wprowadzania, a każda edycja jest oznaczona nazwą osoby, która ją wykonała.

![C&#43;&#43; edycja udostępniania na żywo](../ide/media/live-share-edit-cpp.png "Edycja udostępniania na żywo w języku C++")

## <a name="live-share-host-and-guests"></a>Live Share host i goście

W sesji udostępniania na żywo jest gospodarz i jeden lub więcej osób. Zarówno host, jak i goście mogą używać programu Visual Studio lub visual studio code. Host programu Visual Studio 2019 w systemie Windows może współużytkować z gościem kodu programu Visual Studio w systemie Linux.

Gospodarz zapewnia gościom wszystko, czego potrzebują, aby być produktywnym. Goście nie muszą mieć kodu źródłowego, kompilatora, zależności zewnętrznych lub nawet tych samych zainstalowanych składników.

Gospodarz i goście mogą korzystać z następujących funkcji IntelliSense:

- Lista członków
- Pomoc dotycząca parametrów
- Szybkie informacje
- Debugowanie/punkty przerwania
- Znajdź wszystkie odwołania
- Przejdź do definicji
- Wyszukiwanie symboli (Ctrl+T)
- Wyróżnianie odwołań
- Diagnostyka/Błędy/Squiggles

![C&#43;&#43; debugowanie udostępniania na żywo](../ide/media/live-share-debug-cpp.png "Debugowanie udostępniania na żywo w języku C++")

## <a name="start-and-end-a-live-share-session"></a>Rozpoczynanie i kończynie sesji udostępniania na żywo

Aby rozpocząć sesję udostępniania na żywo w programie Visual Studio, kliknij przycisk Udostępnij w prawym górnym rogu lub przejdź do **aplikacji File** > **Start Collaboration Session**. Spowoduje to wygenerowanie łącza, które można udostępnić współpracownikom.

![C&#43;&#43; przycisk udostępniania na żywo](../ide/media/live-share-button-cpp.png "Przycisk Udostępniania na żywo")

Aby zakończyć sesję, wybierz pozycję **Zakończ sesję współpracy** z listy rozwijanej **Udostępnianie.**

![C&#43;&#43; przycisk udostępniania na żywo](../ide/media/live-share-end-session-cpp.png "Przycisk Udostępniania na żywo")

## <a name="for-more-information"></a>Więcej informacji

Aby uzyskać więcej informacji na temat **udostępniania na żywo** w programie Visual Studio, zobacz Co to jest udostępnianie na żywo programu Visual [Studio?](/visualstudio/liveshare/). Aby uzyskać więcej informacji na temat udostępniania na żywo w programie Visual Studio Code, zobacz [Udostępnianie na żywo](https://marketplace.visualstudio.com/items?itemName=ms-vsliveshare.vsliveshare).

## <a name="see-also"></a>Zobacz też

[Kod edycji i refaktoryzacji (C++)](writing-and-refactoring-code-cpp.md)</br>
[Poruszanie się po bazie kodu języka C++ w programie Visual Studio](navigate-code-cpp.md)</br>
[Czytanie i interpretacja kodu w języku C++](read-and-understand-code-cpp.md)</br>
