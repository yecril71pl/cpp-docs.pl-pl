---
title: Udostępnianie ani nie używaj ponownie ustawienia projektu programu Visual Studio — C++
ms.date: 03/27/2019
helpviewer_keywords:
- project properties [C++], reusable
ms.openlocfilehash: b49c125e0341a2de68bbcd992dd8f9afaa99233d
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565129"
---
# <a name="share-or-reuse-visual-studio-project-settings"></a>Udostępnianie ani nie używaj ponownie ustawienia projektu programu Visual Studio

Aby utworzyć niestandardowe grupy ustawień, które można udostępniać innym użytkownikom lub ponownego użycia w wielu projektach, użyj **Menedżer właściwości** utworzyć *arkusza właściwości* (plik .props) do przechowywania ustawień dla każdego rodzaju Projekt, który chcesz mieć możliwość ponownego użycia lub udostępnienia innym osobom. Przy użyciu właściwości arkusze są znacznie mniej podatne na błędy niż inne sposoby tworzenia "ustawienia"globalne". 

> [!IMPORTANT]
> **pliki .user i kwestia ich problematyczności**
>
> Poprzednich wersji programu Visual Studio używały arkuszy właściwości globalnych, które miały rozszerzenie nazwy pliku .user i znajdowały się w \<userprofile > \AppData\Local\Microsoft\MSBuild\v4.0\ folder. Firma Microsoft nie zaleca już używania tych plików, ponieważ ustawiają one właściwości konfiguracji projektu dla poszczególnych użytkowników i konkretnych komputerów. Takie ustawienia „globalne” mogą zakłócać kompilacje, zwłaszcza gdy są one ukierunkowane na więcej niż jedną platformę na komputerze kompilacji. Na przykład, jeśli masz zarówno projekt MFC, jak i projekt Windows Phone, właściwości .user byłyby nieprawidłowe dla jednego z nich. Arkusze właściwości wielokrotnego użytku są bardziej elastyczne i bardziej niezawodne.
>
> Pomimo tego, że pliki .user są nadal instalowane przez Visual Studio i uczestniczą w dziedziczeniu właściwości, są one domyślnie puste. Najlepszym rozwiązaniem jest usunięcie odwołania do nich w **Menedżer właściwości** w celu zapewnienia, że projekty będą działać niezależnie od dowolnego użytkownika, ustawienia to ważne jest zapewnienie poprawnego zachowania w SCC (kod źródłowy środowisko Control).

Aby wyświetlić **Menedżer właściwości**, na pasku menu wybierz **widoku**, **Windows inne**, **Menedżer właściwości**.

Jeśli masz wspólny, często używany zestaw właściwości, które chcesz zastosować do wielu projektów, możesz użyć **Menedżer właściwości** aby uchwycić je w do ponownego użycia *arkusza właściwości* pliku, który zwyczajowo ma rozszerzenie nazwy pliku .props. Arkusz (lub arkusze) można stosować do nowych projektów, aby nie było konieczne ustawianie ich właściwości od podstaw. Aby uzyskać dostęp do **Menedżer właściwości**, na pasku menu wybierz **widoku**, **Menedżer właściwości**.

![Menu skrótów Menedżer właściwości](media/sharingnew.png "SharingNew")

W każdym węźle konfiguracji zobaczysz węzłów dla każdego arkusza właściwości, która ma zastosowanie do konfiguracji. System dodaje arkuszy właściwości, które ustawić wartości na podstawie opcji wybranych w Kreatorze aplikacji, podczas tworzenia projektu. Kliknij prawym przyciskiem myszy dowolny węzeł, a następnie wybierz polecenie Właściwości, aby wyświetlić właściwości, które są stosowane do tego węzła. Wszystkie arkusze właściwości są automatycznie importowane do arkusza właściwości "główną" projektu (ms.cpp.props) i są obliczane w kolejności, w jakiej znajdują się w Menedżerze właściwości. Możesz przenieść je, aby zmienić kolejność oceny. Arkusze właściwości, które zostaną później ocenione spowoduje zastąpienie wartości w arkuszach wcześniej obliczane. Zobacz [projektu dziedziczenia właściwości](project-property-inheritance.md) Aby uzyskać więcej informacji na temat kolejność obliczania w pliku .vcxproj, pliki .props i .targets, zmienne środowiskowe i wiersza polecenia.

Jeśli wybierzesz **Dodaj nowy arkusz właściwości projektu** i następnie wybierzesz na przykład arkusz właściwości MyProps.props, okno dialogowe strony właściwości jest wyświetlana. Należy zauważyć, że ma ona zastosowanie do arkusza właściwości MyProps; wszelkie wprowadzone zmiany są zapisywane w arkuszu, a nie w pliku projektu (.vcxproj).

Właściwości w arkuszu właściwości zostaną zastąpione, jeśli ustawiono tę samą właściwość bezpośrednio w pliku .vcxproj.

Można importować arkusz własności tak często, jak jest to wymagane. Wiele projektów w rozwiązaniu może dziedziczyć ustawienia z tego samego arkusza właściwości, a projekt może mieć wiele arkuszy. Arkusz właściwości może dziedziczyć ustawienia z innego arkusza właściwości.

Można również utworzyć jeden arkusz właściwości dla wielu konfiguracji. W tym celu należy utworzyć arkusz właściwości dla każdej konfiguracji, otwórz menu skrótów dla jednej z nich, wybierz polecenie **Dodaj istniejący arkusz właściwości**, a następnie dodaj inne arkusze. Jednak jeśli używasz jednego wspólnego arkusza właściwości, należy pamiętać, że po ustawieniu właściwości jest ona ustawiana dla wszystkich konfiguracji, których dotyczy arkusz, a środowisko IED nie pokazuje, które projekty lub inne arkusze właściwości dziedziczą z danego arkusza właściwości.

W dużych rozwiązaniach, które będą miały wiele projektów, może być przydatne utworzenie arkusza właściwości na poziomie rozwiązania. Po dodaniu projektu do rozwiązania, użyj **Menedżer właściwości** Dodaj arkusz właściwości do projektu. Jeśli jest to wymagane na poziomie projektu, można dodać nowy arkusz właściwości do ustawiania wartości specyficznych dla projektu.

> [!IMPORTANT]
> Domyślnie plik .props nie uczestniczy w kontroli źródła, ponieważ nie jest utworzony jako element projektu. Można ręcznie dodać plik jako element rozwiązania, jeżeli chce się go włączyć do kontroli źródła.

#### <a name="to-create-a-property-sheet"></a>Aby utworzyć arkusz właściwości

1. Na pasku menu wybierz **widoku**, **Menedżer właściwości**. **Menedżer właściwości** zostanie otwarty.

2. Aby zdefiniować zakres arkusza właściwości, wybierz element, do którego ma to zastosowanie. Może to być określona konfiguracja lub inny arkusz właściwości. Otwórz menu skrótów dla tego elementu, a następnie wybierz **Dodaj nowy arkusz właściwości projektu**. Określ nazwę i lokalizację.

3. W **Menedżer właściwości**, otwórz nowy arkusz właściwości, a następnie ustaw właściwości, które chcesz dołączyć.
