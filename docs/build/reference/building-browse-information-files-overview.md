---
title: 'Kompilowanie plików przeglądania informacji: Przegląd'
ms.date: 05/06/2019
helpviewer_keywords:
- .bsc files, about .bsc files
- bsc files, about bsc files
- browse information files (.bsc)
- browse information files (.bsc), creating
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
ms.openlocfilehash: ffacb7aaf9ac1f7ad6fc4cf12ab479099dc57725
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320669"
---
# <a name="building-browse-information-files-overview"></a>Kompilowanie plików przeglądania informacji: Przegląd

> [!WARNING]
> Mimo że BSCMAKE jest nadal zainstalowany w programie Visual Studio, nie jest już używany przez IDE. Od programu Visual Studio 2008 informacje o przeglądaniu i symbolach są automatycznie przechowywane w pliku sdf programu SQL Server w folderze rozwiązania.

Aby utworzyć informacje przeglądania symboli, kompilator tworzy plik .sbr dla każdego pliku źródłowego w projekcie, a następnie BSCMAKE. EXE łączy pliki .sbr w jeden plik .bsc.

Generowanie plików .sbr i .bsc wymaga czasu, więc program Visual Studio domyślnie wyłącza te funkcje. Jeśli chcesz przeglądać bieżące informacje, musisz włączyć opcje przeglądania i ponownie utworzyć projekt.

Użyj [/FR](fr-fr-create-dot-sbr-file.md) lub [/Fr,](fr-fr-create-dot-sbr-file.md) aby poinformować kompilator o utworzeniu plików .sbr. Aby utworzyć pliki .bsc, można wywołać [BSCMAKE](bscmake-command-line.md) z wiersza polecenia. Korzystanie Z BSCMAKE z wiersza polecenia daje bardziej precyzyjną kontrolę nad manipulowaniem plikami informacji przeglądania. Zobacz [BSCMAKE Reference, aby](bscmake-reference.md) uzyskać więcej informacji.

> [!TIP]
> Generowanie plików .sbr można włączyć, ale pozostawić wyłączenie generowania plików .bsc. Zapewnia to szybkie kompilacje, ale także umożliwia szybkie tworzenie świeżego pliku .bsc, włączając generowanie plików .bsc i tworzenie projektu.

Można skrócić czas, pamięć i miejsce na dysku wymagane do utworzenia pliku bsc, zmniejszając rozmiar pliku .bsc.

Zobacz [General Property Page (Project),](general-property-page-project.md) aby uzyskać informacje na temat tworzenia pliku przeglądarki w środowisku programistycznym.

### <a name="to-create-a-smaller-bsc-file"></a>Aby utworzyć mniejszy plik bsc

1. Użyj [opcji wiersza polecenia BSCMAKE,](bscmake-options.md) aby wykluczyć informacje z pliku informacji przeglądania.

1. Pomiń symbole lokalne w jednym lub więcej plikach .sbr podczas kompilowania lub składania.

1. Jeśli plik obiektu nie zawiera informacji potrzebnych do bieżącego etapu debugowania, należy pominąć jego plik .sbr z polecenia BSCMAKE podczas przebudowy pliku informacji przeglądania.

### <a name="to-combine-the-browse-information-from-several-projects-into-one-browser-file-bsc"></a>Aby połączyć informacje o przeglądaniu z kilku projektów w jeden plik przeglądarki (bsc)

1. Albo nie buduj pliku .bsc na poziomie projektu, albo użyj przełącznika /n, aby zapobiec obcięciu plików .sbr.

1. Po wszystkich projektach są budowane, uruchom BSCMAKE ze wszystkimi plikami .sbr jako dane wejściowe. Akceptowane są symbole wieloznaczne. Na przykład, jeśli katalogi projektów C:\X, C:\Y i C:\Z z plikami .sbr i chcesz połączyć je wszystkie w jeden plik .bsc, a następnie użyć BSCMAKE C:\X\\\*.sbr C:\Y\\\*.sbr C:\Z\\\*.sbr /o c:\whatever_directory\combined.bsc do zbudowania połączonego pliku .bsc.

## <a name="see-also"></a>Zobacz też

[Dodatkowe narzędzia do budowania MSVC](c-cpp-build-tools.md)<br/>
[BSCMAKE — dokumentacja](bscmake-reference.md)
