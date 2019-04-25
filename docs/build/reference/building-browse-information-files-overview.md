---
title: 'Kompilowanie plików przeglądania informacji: Omówienie'
ms.date: 11/04/2016
helpviewer_keywords:
- .bsc files, about .bsc files
- bsc files, about bsc files
- browse information files (.bsc)
- browse information files (.bsc), creating
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
ms.openlocfilehash: 4f12bd25ca3ab718a845dbb04aba3169cc6d4b19
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272887"
---
# <a name="building-browse-information-files-overview"></a>Kompilowanie plików przeglądania informacji: Omówienie

Aby utworzyć dane przeglądania do przeglądania symboli, kompilator tworzy plik SBR dla każdego pliku źródłowego w projekcie, a następnie BSCMAKE. Plik EXE łączy pliki SBR w jednym pliku .bsc.

Generowanie plików SBR i .bsc trwa pewien czas, dlatego Visual C++ wyłącza funkcje te domyślnie. Jeśli chcesz przeglądać bieżące informacje, należy włączyć opcje przeglądania i ponownie skompiluj projekt.

Użyj [/FR](fr-fr-create-dot-sbr-file.md) lub [/Fr](fr-fr-create-dot-sbr-file.md) aby poinformować kompilator, aby utworzyć pliki .sbr. Aby utworzyć pliki .bsc, można wywołać [BSCMAKE](bscmake-command-line.md) z wiersza polecenia. Z poziomu wiersza polecenia przy użyciu BSCMAKE zapewnia bardziej precyzyjną kontrolę nad manipulowania plików przeglądania informacji. Zobacz [odwołanie BSCMAKE](bscmake-reference.md) Aby uzyskać więcej informacji.

> [!TIP]
>  Możesz włączyć Generowanie pliku SBR, ale pozostaw wyłączone Generowanie pliku .bsc. Dzięki temu można szybko kompilacji, ale również pozwala na szybkie tworzenie pliku .bsc świeże przez włączenie generowania pliku .bsc i skompilowanie projektu.

Można zmniejszyć czas, pamięci i miejsca na dysku wymagane do utworzenia pliku .bsc przez zmniejszenie rozmiaru pliku .bsc.

Zobacz [strona właściwości ogólnych (projekt)](general-property-page-project.md) informacji na temat tworzenia pliku przeglądarki w środowisku programistycznym.

### <a name="to-create-a-smaller-bsc-file"></a>Aby utworzyć mniejszy plik .bsc

1. Użyj [opcje wiersza polecenia BSCMAKE](bscmake-options.md) wyłączenie informacji z pliku informacyjnego przeglądarki.

1. Pomiń symbole lokalne w jeden lub więcej plików SBR podczas kompilowania lub złożenia.

1. Jeśli plik obiektu nie zawiera informacji potrzebnych do Twojego bieżącego etapu debugowania, należy pominąć jego plik .sbr polecenia BSCMAKE podczas ponownego kompilowania pliku informacyjnego przeglądarki.

### <a name="to-combine-the-browse-information-from-several-projects-into-one-browser-file-bsc"></a>Aby połączyć informacji dotyczących przeglądania z kilku projektów w przeglądarce jeden plik (.bsc)

1. Nie kompilacji pliku BSC na poziomie projektu albo użyj przełącznika /n Aby pliki SBR obcięcia.

1. Po wszystkie projekty są kompilowane, uruchom BSCMAKE w przypadku wszystkich plików SBR, jako dane wejściowe. Symbole wieloznaczne są akceptowane. Na przykład jeśli była katalogi projektu C:\X C:\Y i C:\Z pliki SBR w nich i chcesz, aby połączyć je wszystkie w jednym pliku .bsc, użyj BSCMAKE C:\X\\\*.sbr C:\Y\\\*.sbr C:\Z\\ \*c:\whatever_directory\combined.bsc /o .sbr do kompilacji pliku BSC połączone.

## <a name="see-also"></a>Zobacz także

[MSVC dodatkowe narzędzia do kompilacji](c-cpp-build-tools.md)<br/>
[BSCMAKE — dokumentacja](bscmake-reference.md)
