---
title: 'Kompilowanie plików przeglądania informacji: Przegląd'
ms.date: 05/06/2019
helpviewer_keywords:
- .bsc files, about .bsc files
- bsc files, about bsc files
- browse information files (.bsc)
- browse information files (.bsc), creating
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
ms.openlocfilehash: 94cb5865e56e12f51ef4a8598a5df3fcbe69fa0f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078356"
---
# <a name="building-browse-information-files-overview"></a>Kompilowanie plików przeglądania informacji: Przegląd

> [!WARNING]
> Mimo że usługa BSCMAKE jest nadal zainstalowana z programem Visual Studio, nie jest już używana przez IDE. Od programu Visual Studio 2008 informacje dotyczące przeglądania i symboli są przechowywane automatycznie w pliku SQL Server. sdf w folderze rozwiązania.

Aby utworzyć informacje o przeglądaniu do przeglądania symboli, kompilator tworzy plik. sbr dla każdego pliku źródłowego w projekcie, a następnie BSCMAKE. EXE łączy pliki. sbr w jeden plik. BSC.

Generowanie plików. sbr i. bsc jest czasochłonne, dlatego program Visual Studio domyślnie wyłącza te funkcje. Aby przeglądać bieżące informacje, należy najpierw włączyć opcje przeglądania i skompilować projekt ponownie.

Użyj [/fr](fr-fr-create-dot-sbr-file.md) lub [/fr](fr-fr-create-dot-sbr-file.md) , aby poinformować kompilator, aby utworzył pliki SBR. Aby utworzyć pliki BSC, możesz wywołać [BSCMAKE](bscmake-command-line.md) z wiersza polecenia. Użycie BSCMAKE z wiersza polecenia daje dokładniejszą kontrolę nad manipulowaniem plikami informacji o przeglądaniu. Aby uzyskać więcej informacji, zobacz [BSCMAKE Reference](bscmake-reference.md) .

> [!TIP]
>  Możesz włączyć generowanie plików. sbr, ale pozostawić wyłączone. generacja plików BSC. Pozwala to na szybkie kompilacje, ale również umożliwia szybkie tworzenie świeżych plików. bsc przez włączenie generacji plików BSC i skompilowanie projektu.

Można skrócić czas, pamięć i miejsce na dysku wymagane do skompilowania pliku. bsc przez zmniejszenie rozmiaru pliku BSC.

Zobacz [Ogólne strony właściwości (projekt)](general-property-page-project.md) , aby uzyskać informacje na temat sposobu tworzenia pliku przeglądarki w środowisku deweloperskim.

### <a name="to-create-a-smaller-bsc-file"></a>Aby utworzyć mniejszy plik. bsc

1. Użyj [opcji wiersza polecenia BSCMAKE](bscmake-options.md) , aby wykluczyć informacje z pliku informacji o przeglądaniu.

1. Pomiń symbole lokalne w jednym lub kilku plikach. sbr podczas kompilowania lub asemblera.

1. Jeśli plik obiektu nie zawiera informacji potrzebnych do bieżącego etapu debugowania, Pomiń plik. sbr w poleceniu BSCMAKE podczas odbudowywania pliku informacji o przeglądaniu.

### <a name="to-combine-the-browse-information-from-several-projects-into-one-browser-file-bsc"></a>Aby połączyć informacje o przeglądaniu z kilku projektów w jeden plik przeglądarki (. bsc)

1. Nie Kompiluj pliku BSC na poziomie projektu lub Użyj przełącznika/n, aby zapobiec obcięciu plików. sbr.

1. Po skompilowaniu wszystkich projektów Uruchom polecenie BSCMAKE ze wszystkimi plikami. sbr jako danymi wejściowymi. Symbole wieloznaczne są akceptowane. Na przykład, jeśli masz katalogi projektu C:\X, C:\Y i C:\Z z plikami. sbr w nich i chcesz połączyć je wszystkie w jeden plik. bsc, użyj BSCMAKE C:\x\\\*. sbr C:\Y\\\*. sbr C:\Z\\\*. sbr/o c:\ whatever_directory \combined.bsc, aby skompilować połączony plik. BSC.

## <a name="see-also"></a>Zobacz też

[Dodatkowe narzędzia do kompilacji MSVC](c-cpp-build-tools.md)<br/>
[BSCMAKE — dokumentacja](bscmake-reference.md)
