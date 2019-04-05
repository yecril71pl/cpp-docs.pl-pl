---
title: Uaktualnianie projektów ze starszych wersji programu Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- 32-bit code porting
- upgrading Visual C++ applications, 32-bit code
ms.assetid: 18cdacaa-4742-43db-9e4c-2d9e73d8cc84
ms.openlocfilehash: 41cac1b23d5ab16825891ef654341016958ab826
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59034916"
---
# <a name="upgrading-projects-from-earlier-versions-of-visual-c"></a>Uaktualnianie projektów ze starszych wersji programu Visual C++

W większości przypadków można otworzyć projekt, który został utworzony we wcześniejszej wersji programu Visual Studio. Jednak w takim przypadku Visual Studio uaktualnia projekt. Jeśli zapiszesz uaktualniony projekt, nie będzie go można otworzyć w starszej wersji.

> [!IMPORTANT]
> Jeśli próbujesz konwertować projekt, który został już przekonwertowany, Visual Studio wyświetla prośbę o potwierdzenie, ponieważ ponowna konwersja usuwa istniejące pliki.

Wiele uaktualnionych projektów i rozwiązań można skompilować bez modyfikacji. Jednak niektóre projekty mogą wymagać zmian ustawień i/lub kodu źródłowego. Warto się posłużyć następującymi wytycznymi, aby najpierw rozwiązać problemy z ustawieniami, a potem, jeśli projektu dalej nie da się skompilować, można rozwiązać problemy z kodem. Aby uzyskać więcej informacji, zobacz [omówienie potencjalnych problemów z uaktualnieniem](../porting/overview-of-potential-upgrade-issues-visual-cpp.md).

1. Utwórz kopię istniejących plików projektu i rozwiązania. Zainstaluj aktualną wersję Visual Studio i starszą wersję obok siebie, tak aby w razie potrzeby można było porównać wersje plików.

2. W aktualnej wersji Visual Studio, otwórz — a tym samym uaktualnij — kopię projektu lub rozwiązania i zapisz ją.

3. Dla każdego przekonwertowanego projektu, otwórz menu skrótów i wybierz polecenie **właściwości**. W obszarze **właściwości konfiguracji**, wybierz opcję **ogólne** i następnie **zestawu narzędzi platformy**, wybierz bieżącą wersję. (Na przykład dla programu Visual Studio 2017, wybierz pozycję **wersji 141**.)

4. Skompiluj rozwiązanie. Jeżeli kompilacja zakończy się niepowodzeniem, zmodyfikuj ustawienia i zrekompiluj.

Źródła danych są zawarte w oddzielnym projekcie bazy danych, tak że można łatwo modyfikować i debugować procedury zapisane w tych źródłach. W przypadku uaktualniania projektu C++, który zawiera źródła danych, automatycznie jest tworzony oddzielny projekt bazy danych.

Aby uzyskać informacje o tym, jak można zaktualizować docelowej wersji Windows, zobacz [modyfikowanie WINVER i _WIN32_WINNT](../porting/modifying-winver-and-win32-winnt.md).

## <a name="in-this-section"></a>W tej sekcji

[Uaktualnienie kodu do Universal CRT](upgrade-your-code-to-the-universal-crt.md)<br/>
[Modyfikowanie symboli WINVER i _WIN32_WINNT](modifying-winver-and-win32-winnt.md)<br/>
[Naprawianie zależności w bibliotece wewnętrznej](fix-your-dependencies-on-library-internals.md)<br/>
[Problemy dotyczące migracji liczb zmiennoprzecinkowych](floating-point-migration-issues.md)<br/>
[Użyj natywnej wielowersyjności kodu w programie Visual Studio do kompilacji starych projektów](use-native-multi-targeting.md)<br/>
[Funkcje programu Visual C++ uznane za przestarzałe w wersji zapoznawczej programu Visual Studio 2019 r.](features-deprecated-in-visual-studio.md)<br/>
[Zmiany systemu kompilacji](build-system-changes.md)<br/>

## <a name="see-also"></a>Zobacz także

[Co nowego w języku Visual C++ w programie Visual Studio 2017](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
[Visual C++ — Historia latach 2003 – 2015 zmian](../porting/visual-cpp-change-history-2003-2015.md)<br/>
[Niestandardowe zachowanie](../cpp/nonstandard-behavior.md)
