---
title: Współpracuj z udostępnianie na żywo dla C++ w programie Visual Studio
description: Użyj, funkcja udostępniania na żywo dla C++ w programie Visual Studio do współpracy i udostępniania kodu w czasie rzeczywistym.
ms.date: 05/24/2019
ms.openlocfilehash: 8886bb3ea4b7389a9d6953655e2dc6ccfa1c7c9a
ms.sourcegitcommit: 65ed563a8a1d4d90f872a2a6edcb086f84ec9f77
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66743394"
---
# <a name="collaborate-using-live-share-for-c"></a>Bezpieczna współpraca przy użyciu funkcja udostępniania na żywo dlaC++

W Visual Studio 2019 r i Visual Studio Code, można użyć **udostępniania na żywo** do współpracy nad C++ projektów w czasie rzeczywistym. Za pomocą **udostępniania na żywo** innej osobie można edytować i debugowanie kodu bez konieczności instalowania projektu lub dowolną z jego zależności. Występują one, a każdy edytowanie zostanie oznaczony o nazwie osoby, która mogła zostanie wyświetlona jego edycji. 

![C&#43; &#43; udziału edytowanie na żywo](../ide/media/live-share-edit-cpp.png "edytowanie na żywo udziałuC++")

## <a name="live-share-host-and-guests"></a>Na żywo udziału hostów i gości

W sesji udostępniania na żywo ma hosta i co najmniej jeden gości. Zarówno hosta, jak i gości, można użyć programu Visual Studio lub Visual Studio Code. Visual Studio 2019 hosta, na Windows mogą udostępniać gościa programu Visual Studio Code w systemie Linux.

Host zawiera gościom ze wszystkim, co jest potrzebne do wydajnej. Goście nie muszą mieć kod źródłowy, kompilator, zależnościami zewnętrznymi lub nawet sam zainstalowanych składników. 

Hostów i gości można korzystać z funkcji IntelliSense: 

- Lista elementów członkowskich
- Parametr pomocy
- Szybkie informacje
- Debugowanie/punktów przerwania
- Znajdź wszystkie odwołania
- Przejdź do definicji
- Wyszukiwanie symbolu (Ctrl + T)
- Wyróżnianie odwołań
- Diagnostyka/błędy/faliste linie

![C&#43; &#43; udziału debugowania na żywo](../ide/media/live-share-debug-cpp.png "mieszka udziału debugowaniaC++")

## <a name="start-and-end-a-live-share-session"></a>Uruchamianie i kończenie sesji udostępniania na żywo

Aby rozpocząć sesję udostępniania na żywo w programie Visual Studio, kliknij przycisk Udostępnij w prawym górnym lub przejdź do **pliku** > **Uruchom sesję współpracy**. Spowoduje to wygenerowanie łącze, które mogą udostępniać swoje współpracowników.

![C&#43; &#43; Live przycisk Udostępnij](../ide/media/live-share-button-cpp.png "Live przycisk Udostępnij")

Aby zakończyć sesję, wybierz pozycję **Zakończ sesję współpracy** z **udostępniania** listy rozwijanej.

![C&#43; &#43; Live przycisk Udostępnij](../ide/media/live-share-end-session-cpp.png "Live przycisk Udostępnij")

## <a name="for-more-information"></a>Więcej informacji

Aby uzyskać więcej informacji na temat **udostępniania na żywo** w programie Visual Studio, zobacz [co to jest Visual Studio funkcja udostępniania na żywo?](/visualstudio/liveshare/). Aby uzyskać więcej informacji na temat udostępniania na żywo w programie Visual Studio Code, zobacz [ udostępniania na żywo](https://marketplace.visualstudio.com/items?itemName=ms-vsliveshare.vsliveshare).

## <a name="see-also"></a>Zobacz też

[Edytuj i refaktoryzacji kodu (C++)](writing-and-refactoring-code-cpp.md)</br>
[Przejdź z C++ kodu bazowego w programie Visual Studio](navigate-code-cpp.md)</br>
[Dokładnie zapoznaj się C++ kodu](read-and-understand-code-cpp.md)</br>