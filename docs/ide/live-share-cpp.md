---
title: Współpraca z Live Shareami dla języka C++ w programie Visual Studio
description: Użyj Live Share dla języka C++ w programie Visual Studio, aby współpracować i udostępniać kod w czasie rzeczywistym.
ms.date: 05/24/2019
ms.openlocfilehash: 60830ad6c6b98f644e1c3ddb2e78fbf7397ae919
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684524"
---
# <a name="collaborate-using-live-share-for-c"></a>Współpraca przy użyciu rozszerzenia Live Share dla języka C++

W programie Visual Studio 2019 i Visual Studio Code można używać **Live Share** do współpracy z projektami C++ w czasie rzeczywistym. Za pomocą **Live Share** inna osoba może edytować i debugować kod bez konieczności instalowania projektu lub żadnej z jego zależności. Wszystkie zmiany są widoczne w miarę ich występowania, a każda Edycja jest oznaczona nazwą osoby, która ją wprowadziła.

![Live Share&#43;&#43; edycji języka C](../ide/media/live-share-edit-cpp.png "Edytowanie Live Share w języku C++")

## <a name="live-share-host-and-guests"></a>Live Share hosta i Gości

W sesji Live Share istnieje Host i co najmniej jeden gość. Zarówno host, jak i Goście mogą korzystać z programu Visual Studio lub Visual Studio Code. Host programu Visual Studio 2019 w systemie Windows może udostępniać Visual Studio Code gościa w systemie Linux.

Host udostępnia Gościom wszystko, czego potrzebują do pracy. Goście nie muszą mieć kodu źródłowego, kompilatora, zależności zewnętrznych, a nawet tych samych zainstalowanych składników.

Host i Goście mogą korzystać z tych funkcji IntelliSense:

- Lista elementów członkowskich
- Pomoc dotycząca parametrów
- Szybkie informacje
- Debugowanie/punkty przerwania
- Znajdź wszystkie odwołania
- Przejdź do definicji
- Wyszukiwanie symboli (Ctrl + T)
- Wyróżnianie odwołań
- Diagnostyka/błędy/zygzaki

![Debugowanie w języku C&#43;&#43; Live Share](../ide/media/live-share-debug-cpp.png "Debugowanie Live Share w języku C++")

## <a name="start-and-end-a-live-share-session"></a>Uruchamianie i kończenie sesji Live Share

Aby rozpocząć sesję Live Share w programie Visual Studio, kliknij przycisk Udostępnij w prawym górnym rogu lub przejdź do **pliku**  >  **Rozpocznij sesję współpracy**. Spowoduje to wygenerowanie linku, który można udostępnić współpracownikom.

![Niewielki zrzut ekranu przycisku Live Share.](../ide/media/live-share-button-cpp.png "Przycisk Live Share")

Aby zakończyć sesję, wybierz pozycję **Zakończ sesję współpracy** z listy rozwijanej **udostępnianie** .

![Zrzut ekranu przedstawiający listę rozwijaną udostępniania z wyróżnioną opcją sesji współpracy końcowej.](../ide/media/live-share-end-session-cpp.png "Przycisk Live Share")

## <a name="for-more-information"></a>Więcej informacji

Aby uzyskać więcej informacji na temat **Live Share** w programie Visual Studio, zobacz [co to jest Visual Studio Live Share?](/visualstudio/liveshare/). Aby uzyskać więcej informacji na temat Live Share w Visual Studio Code, zobacz [ Live Share](https://marketplace.visualstudio.com/items?itemName=ms-vsliveshare.vsliveshare).

## <a name="see-also"></a>Zobacz też

[Edytuj i Refaktoryzacja kodu (C++)](writing-and-refactoring-code-cpp.md)</br>
[Nawigowanie po bazie kodu C++ w programie Visual Studio](navigate-code-cpp.md)</br>
[Czytanie i interpretacja kodu w języku C++](read-and-understand-code-cpp.md)</br>
