---
title: Udostępnianie lub ponowne używanie ustawień projektu programu Visual Studio —C++
ms.date: 07/17/2019
helpviewer_keywords:
- project properties [C++], reusable
ms.openlocfilehash: 451e22997f81753abf0c8d55d3b9e8d097cc6d5d
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078707"
---
# <a name="share-or-reuse-visual-studio-project-settings"></a>Udostępnianie lub ponowne używanie ustawień projektów programu Visual Studio

Aby utworzyć niestandardową grupę ustawień, które można udostępniać innym osobom lub użyć ich ponownie w wielu projektach, użyj **Menedżer właściwości** , aby utworzyć *Arkusz właściwości* (. props) do przechowywania ustawień dla każdego rodzaju projektu, które mają być możliwe do ponownego użycia lub udostępnienia innym osobom. Używanie arkuszy właściwości jest znacznie mniej podatne na błędy niż inne sposoby tworzenia ustawień globalnych.

> [!IMPORTANT]
> **pliki. User i dlaczego są problematyczne**
>
> Poprzednie wersje programu Visual Studio używały globalnych arkuszy właściwości, które mają rozszerzenie nazwy pliku. User i znajdowały się w folderze \<USERPROFILE > \AppData\Local\Microsoft\MSBuild\v4.0\. Firma Microsoft nie zaleca już używania tych plików, ponieważ ustawiają one właściwości konfiguracji projektu dla poszczególnych użytkowników i konkretnych komputerów. Takie ustawienia „globalne” mogą zakłócać kompilacje, zwłaszcza gdy są one ukierunkowane na więcej niż jedną platformę na komputerze kompilacji. Na przykład, jeśli masz zarówno projekt MFC, jak i projekt Windows Phone, właściwości .user byłyby nieprawidłowe dla jednego z nich. Arkusze właściwości wielokrotnego użytku są bardziej elastyczne i bardziej niezawodne.
>
> Pomimo tego, że pliki .user są nadal instalowane przez Visual Studio i uczestniczą w dziedziczeniu właściwości, są one domyślnie puste. Najlepszym rozwiązaniem jest usunięcie odwołania do nich w **Menedżer właściwości** , aby upewnić się, że projekty działają niezależnie od wszelkich ustawień dla poszczególnych użytkowników i komputerów, jest to ważne, aby zapewnić poprawne zachowanie w środowisku SCC (kontroli kodu źródłowego).

Aby wyświetlić **Menedżer właściwości**, na pasku menu wybierz pozycję **Wyświetl** > **Menedżer właściwości** lub **Wyświetl** > **innych > systemu Windows** **Menedżer właściwości, w**zależności od ustawień.

Jeśli masz wspólny, często używany zestaw właściwości, które chcesz zastosować do wielu projektów, możesz użyć **Menedżer właściwości** do przechwycenia ich w pliku *arkusza właściwości* wielokrotnego użytku, który Konwencji ma rozszerzenie nazwy pliku. props. Arkusz (lub arkusze) można stosować do nowych projektów, aby nie było konieczne ustawianie ich właściwości od podstaw.

![Menedżer właściwości menu skrótów](media/sharingnew.png "SharingNew")

W każdym węźle konfiguracji są wyświetlane węzły dla każdego arkusza właściwości, który ma zastosowanie do tej konfiguracji. System dodaje arkusze właściwości, które ustawiają wartości na podstawie opcji wybranych w Kreatorze aplikacji podczas tworzenia projektu. Kliknij prawym przyciskiem myszy dowolny węzeł i wybierz polecenie Właściwości, aby wyświetlić właściwości, które mają zastosowanie do tego węzła. Wszystkie arkusze właściwości są importowane automatycznie do arkusza właściwości projektu "Master" (MS. cpp. props) i są oceniane w kolejności, w jakiej występują w Menedżer właściwości. Można je przenieść, aby zmienić kolejność szacowania. Arkusze właściwości, które są oceniane później, przesłonią wartości w poprzednio ocenionych arkuszach. Zobacz [dziedziczenie właściwości projektu](project-property-inheritance.md) , aby uzyskać więcej informacji na temat kolejności oceny w pliku. vcxproj, pliki. props i. targets, zmienne środowiskowe i wiersz polecenia.

Jeśli wybierzesz opcję **Dodaj nowy arkusz właściwości projektu** , a następnie wybierzesz na przykład arkusz właściwości webprops. props, pojawi się okno dialogowe strony właściwości. Należy zauważyć, że ma ona zastosowanie do arkusza właściwości MyProps; wszelkie wprowadzone zmiany są zapisywane w arkuszu, a nie w pliku projektu (.vcxproj).

Właściwości w arkuszu właściwości zostaną zastąpione, jeśli ustawiono tę samą właściwość bezpośrednio w pliku .vcxproj.

Można importować arkusz własności tak często, jak jest to wymagane. Wiele projektów w rozwiązaniu może dziedziczyć ustawienia z tego samego arkusza właściwości, a projekt może mieć wiele arkuszy. Arkusz właściwości może dziedziczyć ustawienia z innego arkusza właściwości.

Można również utworzyć jeden arkusz właściwości dla wielu konfiguracji. W tym celu Utwórz arkusz właściwości dla każdej konfiguracji, otwórz menu skrótów dla jednego z nich, wybierz polecenie **Dodaj istniejący arkusz właściwości**, a następnie Dodaj inne arkusze. Jednak jeśli używasz jednego wspólnego arkusza właściwości, należy pamiętać, że po ustawieniu właściwości jest ona ustawiana dla wszystkich konfiguracji, do których odnosi się arkusz, i że IDE nie pokazuje, które projekty lub inne arkusze właściwości są dziedziczone z danego arkusza właściwości.

W dużych rozwiązaniach, które będą miały wiele projektów, może być przydatne utworzenie arkusza właściwości na poziomie rozwiązania. Po dodaniu projektu do rozwiązania, użyj **Menedżer właściwości** , aby dodać ten arkusz właściwości do projektu. Jeśli jest to wymagane na poziomie projektu, można dodać nowy arkusz właściwości do ustawiania wartości specyficznych dla projektu.

> [!IMPORTANT]
> Domyślnie plik. props nie uczestniczy w kontroli źródła, ponieważ nie jest utworzony jako element projektu. Można ręcznie dodać plik jako element rozwiązania, jeżeli chce się go włączyć do kontroli źródła.

#### <a name="to-create-a-property-sheet"></a>Aby utworzyć arkusz właściwości

1. Na pasku menu wybierz polecenie **wyświetl** > **Menedżer właściwości** lub **Wyświetl** > inne > **Menedżer właściwości** **systemu Windows** . Zostanie otwarty **Menedżer właściwości** .

2. Aby zdefiniować zakres arkusza właściwości, wybierz element, do którego ma to zastosowanie. Może to być określona konfiguracja lub inny arkusz właściwości. Otwórz menu skrótów dla tego elementu, a następnie wybierz polecenie **Dodaj nowy projekt arkusza właściwości**. Określ nazwę i lokalizację.

3. W **Menedżer właściwości**Otwórz nowy arkusz właściwości, a następnie ustaw właściwości, które chcesz uwzględnić.
