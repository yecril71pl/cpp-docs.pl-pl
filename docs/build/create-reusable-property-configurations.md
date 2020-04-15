---
title: Udostępnianie lub ponowne używanie ustawień projektu programu Visual Studio — C++
ms.date: 07/17/2019
helpviewer_keywords:
- project properties [C++], reusable
ms.openlocfilehash: bcf54be0531c7150c1506eb6f5dda2b5bc95161f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328689"
---
# <a name="share-or-reuse-visual-studio-project-settings"></a>Udostępnianie lub ponowne używanie ustawień projektów programu Visual Studio

Aby utworzyć niestandardową grupę ustawień, którą można udostępnić innym osobom lub ponownie użyć w wielu projektach, użyj **Menedżera właściwości,** aby utworzyć *arkusz właściwości* (plik props), aby zapisać ustawienia dla każdego rodzaju projektu, który ma być ponownie użyty lub udostępnić innym osobom. Korzystanie z arkuszy właściwości są znacznie mniej podatne na błędy niż inne sposoby tworzenia "globalnych" ustawień.

> [!IMPORTANT]
> **.user files i dlaczego są one problematyczne**
>
> Poprzednie wersje programu Visual Studio używały globalnych arkuszy właściwości, \<które miały rozszerzenie nazwy pliku .user i znajdowały się w folderze> profilu użytkownika\AppData\Local\Microsoft\MSBuild\v4.0\folder. Firma Microsoft nie zaleca już używania tych plików, ponieważ ustawiają one właściwości konfiguracji projektu dla poszczególnych użytkowników i konkretnych komputerów. Takie ustawienia „globalne” mogą zakłócać kompilacje, zwłaszcza gdy są one ukierunkowane na więcej niż jedną platformę na komputerze kompilacji. Na przykład, jeśli masz zarówno projekt MFC, jak i projekt Windows Phone, właściwości .user byłyby nieprawidłowe dla jednego z nich. Arkusze właściwości wielokrotnego użytku są bardziej elastyczne i bardziej niezawodne.
>
> Pomimo tego, że pliki .user są nadal instalowane przez Visual Studio i uczestniczą w dziedziczeniu właściwości, są one domyślnie puste. Najlepszym rozwiązaniem jest usunięcie odwołania do nich w **Menedżerze właściwości,** aby upewnić się, że projekty działają niezależnie od wszelkich ustawień na użytkownika, na komputerze Jest to ważne, aby zapewnić poprawne zachowanie w środowisku SCC (kontrola kodu źródłowego).

Aby wyświetlić **Menedżera właściwości**na pasku menu, wybierz pozycję **Wyświetl** > **Menedżera właściwości** lub **Wyświetl** > inny**Menedżer właściwości**systemu**Windows** > , w zależności od ustawień.

Jeśli masz wspólny, często używany zestaw właściwości, które chcesz zastosować do wielu projektów, można użyć **Menedżera właściwości,** aby przechwycić je w pliku *arkusza właściwości* wielokrotnego użytku, który zgodnie z konwencją ma rozszerzenie nazwy pliku .props. Arkusz (lub arkusze) można stosować do nowych projektów, aby nie było konieczne ustawianie ich właściwości od podstaw.

![Menu skrótów Menedżera właściwości](media/sharingnew.png "UdostępnianieNowy")

W każdym węźle konfiguracji zobaczysz węzły dla każdego arkusza właściwości, który ma zastosowanie do tej konfiguracji. System dodaje arkusze właściwości, które ustawiają wartości na podstawie opcji wybierane w kreatorze aplikacji podczas tworzenia projektu. Kliknij prawym przyciskiem myszy dowolny węzeł i wybierz polecenie Właściwości, aby wyświetlić właściwości, które mają zastosowanie do tego węzła. Wszystkie arkusze właściwości są importowane automatycznie do arkusza właściwości "master" projektu (ms.cpp.props) i są oceniane w kolejności, w jakiej pojawiają się w Menedżerze właściwości. Można je przenieść, aby zmienić kolejność oceny. Arkusze właściwości, które są oceniane później, zastąpią wartości w wcześniej ocenianych arkuszach. Zobacz [Dziedziczenie właściwości projektu,](project-property-inheritance.md) aby uzyskać więcej informacji na temat kolejności oceny w pliku .vcxproj, plikach .props i .targets, zmiennych środowiskowych i wierszu polecenia.

Jeśli wybierzesz **pozycję Dodaj nowy arkusz właściwości projektu,** a następnie wybierzesz na przykład arkusz właściwości MyProps.props, zostanie wyświetlone okno dialogowe strona właściwości. Należy zauważyć, że ma ona zastosowanie do arkusza właściwości MyProps; wszelkie wprowadzone zmiany są zapisywane w arkuszu, a nie w pliku projektu (.vcxproj).

Właściwości w arkuszu właściwości zostaną zastąpione, jeśli ustawiono tę samą właściwość bezpośrednio w pliku .vcxproj.

Można importować arkusz własności tak często, jak jest to wymagane. Wiele projektów w rozwiązaniu może dziedziczyć ustawienia z tego samego arkusza właściwości, a projekt może mieć wiele arkuszy. Arkusz właściwości może dziedziczyć ustawienia z innego arkusza właściwości.

Można również utworzyć jeden arkusz właściwości dla wielu konfiguracji. Aby to zrobić, utwórz arkusz właściwości dla każdej konfiguracji, otwórz menu skrótów dla jednej z nich, wybierz pozycję **Dodaj istniejący arkusz właściwości,** a następnie dodaj inne arkusze. Jednak jeśli używasz jednego arkusza właściwości wspólnych, należy pamiętać, że po ustawieniu właściwości, pobiera zestaw dla wszystkich konfiguracji, które stosuje się do arkusza i ide nie pokazuje, które projekty lub inne arkusze właściwości dziedziczą z danego arkusza właściwości.

W dużych rozwiązaniach, które będą miały wiele projektów, może być przydatne utworzenie arkusza właściwości na poziomie rozwiązania. Po dodaniu projektu do rozwiązania należy użyć **Menedżera właściwości,** aby dodać ten arkusz właściwości do projektu. Jeśli jest to wymagane na poziomie projektu, można dodać nowy arkusz właściwości do ustawiania wartości specyficznych dla projektu.

> [!IMPORTANT]
> Plik .props domyślnie nie uczestniczy w kontroli źródła, ponieważ nie jest tworzony jako element projektu. Można ręcznie dodać plik jako element rozwiązania, jeżeli chce się go włączyć do kontroli źródła.

#### <a name="to-create-a-property-sheet"></a>Aby utworzyć arkusz właściwości

1. Na pasku menu wybierz pozycję **Wyświetl** > **Menedżera właściwości** lub **Wyświetl** > inny**Menedżer właściwości**systemu**Windows** > . Zostanie otwarty **Menedżer właściwości.**

2. Aby zdefiniować zakres arkusza właściwości, wybierz element, do którego ma to zastosowanie. Może to być określona konfiguracja lub inny arkusz właściwości. Otwórz menu skrótów dla tego elementu, a następnie wybierz pozycję **Dodaj arkusz właściwości nowego projektu**. Określ nazwę i lokalizację.

3. W **Menedżerze właściwości**otwórz nowy arkusz właściwości, a następnie ustaw właściwości, które chcesz uwzględnić.
