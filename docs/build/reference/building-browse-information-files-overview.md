---
title: 'Kompilowanie plików przeglądania informacji: Przegląd | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- .bsc files, about .bsc files
- bsc files, about bsc files
- browse information files (.bsc)
- browse information files (.bsc), creating
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 493f25ba6839058a9ff749cb0dbb3853b1b16494
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712299"
---
# <a name="building-browse-information-files-overview"></a>Kompilowanie plików przeglądania informacji: Przegląd

Aby utworzyć dane przeglądania do przeglądania symboli, kompilator tworzy plik SBR dla każdego pliku źródłowego w projekcie, a następnie BSCMAKE. Plik EXE łączy pliki SBR w jednym pliku .bsc.

Generowanie plików SBR i .bsc trwa pewien czas, dlatego Visual C++ wyłącza funkcje te domyślnie. Jeśli chcesz przeglądać bieżące informacje, należy włączyć opcje przeglądania i ponownie skompiluj projekt.

Użyj [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) lub [/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md) aby poinformować kompilator, aby utworzyć pliki .sbr. Aby utworzyć pliki .bsc, można wywołać [BSCMAKE](../../build/reference/bscmake-command-line.md) z wiersza polecenia. Z poziomu wiersza polecenia przy użyciu BSCMAKE zapewnia bardziej precyzyjną kontrolę nad manipulowania plików przeglądania informacji. Zobacz [odwołanie BSCMAKE](../../build/reference/bscmake-reference.md) Aby uzyskać więcej informacji.

> [!TIP]
>  Możesz włączyć Generowanie pliku SBR, ale pozostaw wyłączone Generowanie pliku .bsc. Dzięki temu można szybko kompilacji, ale również pozwala na szybkie tworzenie pliku .bsc świeże przez włączenie generowania pliku .bsc i skompilowanie projektu.

Można zmniejszyć czas, pamięci i miejsca na dysku wymagane do utworzenia pliku .bsc przez zmniejszenie rozmiaru pliku .bsc.

Zobacz [strona właściwości ogólnych (projekt)](../../ide/general-property-page-project.md) informacji na temat tworzenia pliku przeglądarki w środowisku programistycznym.

### <a name="to-create-a-smaller-bsc-file"></a>Aby utworzyć mniejszy plik .bsc

1. Użyj [opcje wiersza polecenia BSCMAKE](../../build/reference/bscmake-options.md) wyłączenie informacji z pliku informacyjnego przeglądarki.

1. Pomiń symbole lokalne w jeden lub więcej plików SBR podczas kompilowania lub złożenia.

1. Jeśli plik obiektu nie zawiera informacji potrzebnych do Twojego bieżącego etapu debugowania, należy pominąć jego plik .sbr polecenia BSCMAKE podczas ponownego kompilowania pliku informacyjnego przeglądarki.

### <a name="to-combine-the-browse-information-from-several-projects-into-one-browser-file-bsc"></a>Aby połączyć informacji dotyczących przeglądania z kilku projektów w przeglądarce jeden plik (.bsc)

1. Nie kompilacji pliku BSC na poziomie projektu albo użyj przełącznika /n Aby pliki SBR obcięcia.

1. Po wszystkie projekty są kompilowane, uruchom BSCMAKE w przypadku wszystkich plików SBR, jako dane wejściowe. Symbole wieloznaczne są akceptowane. Na przykład jeśli była katalogi projektu C:\X C:\Y i C:\Z pliki SBR w nich i chcesz, aby połączyć je wszystkie w jednym pliku .bsc, użyj BSCMAKE C:\X\\\*.sbr C:\Y\\\*.sbr C:\Z\\ \*c:\whatever_directory\combined.bsc /o .sbr do kompilacji pliku BSC połączone.

## <a name="see-also"></a>Zobacz też

[Narzędzia kompilacji C/C++](../../build/reference/c-cpp-build-tools.md)<br/>
[BSCMAKE — dokumentacja](../../build/reference/bscmake-reference.md)
