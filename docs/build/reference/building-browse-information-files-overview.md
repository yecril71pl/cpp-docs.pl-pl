---
title: 'Tworzenia plików informacji przeglądania: Omówienie | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 6a2306c69c219320e11259ba6303b76588db8f7b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="building-browse-information-files-overview"></a>Kompilowanie plików przeglądania informacji: Przegląd
Aby utworzyć informacje o przeglądaniu do przeglądania symbolu, kompilator tworzy plik SBR dla każdego pliku źródłowego w projekcie, a następnie BSCMAKE. EXE łączy pliki SBR w jednym pliku .bsc.  
  
 Generowanie plików SBR i .bsc jest czasochłonne, więc Visual C++ wyłącza funkcje te domyślnie. Chcesz przeglądać aktualne informacje, należy włączyć opcje przeglądania, ponownie skompilować projekt.  
  
 Użyj [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) lub [/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md) mówić kompilatora, aby utworzyć pliki .sbr. Aby utworzyć pliki .bsc, można wywołać [BSCMAKE](../../build/reference/bscmake-command-line.md) z wiersza polecenia. Korzystanie z wiersza polecenia BSCMAKE zapewnia dokładniejszą kontrolę nad operowanie plików przeglądania informacji. Zobacz [odwołanie BSCMAKE](../../build/reference/bscmake-reference.md) Aby uzyskać więcej informacji.  
  
> [!TIP]
>  Można włączyć Generowanie pliku SBR, ale pozostawić wyłączone Generowanie pliku .bsc. Zapewnia to szybki kompilacje, ale również umożliwia szybkie tworzenie pliku .bsc świeże przez włączenie generowania pliku .bsc i skompilowanie projektu.  
  
 Można ograniczyć czas, pamięci i miejsca na dysku wymagane do utworzenia pliku .bsc przez zmniejszenie rozmiaru pliku .bsc.  
  
 Zobacz [ogólna strona właściwości (projekt)](../../ide/general-property-page-project.md) informacji na temat sposobu tworzenia pliku przeglądarki w środowisku programistycznym.  
  
### <a name="to-create-a-smaller-bsc-file"></a>Aby utworzyć mniejszy plik .bsc  
  
1.  Użyj [opcje wiersza polecenia BSCMAKE](../../build/reference/bscmake-options.md) do wykluczenia informacji z pliku informacyjnego przeglądarki.  
  
2.  Pomiń symbole lokalne w jeden lub więcej plików SBR podczas kompilowania lub zebrania.  
  
3.  Jeśli plik obiektu nie zawiera informacje potrzebne do Twojej bieżący etap debugowania, Pomiń jego plik .sbr polecenia BSCMAKE, podczas odbudowanie pliku informacyjnego przeglądarki.  
  
### <a name="to-combine-the-browse-information-from-several-projects-into-one-browser-file-bsc"></a>Aby połączyć informacje o przeglądaniu z wielu projektów w przeglądarce jednego pliku (.bsc)  
  
1.  Nie kompilacji pliku .bsc na poziomie projektu albo użyj przełącznika /n, aby zapobiec obcinania plików SBR.  
  
2.  Po wszystkie projekty zostały skompilowane, uruchom BSCMAKE ze wszystkich plików SBR, jako dane wejściowe. Symbole wieloznaczne są akceptowane. Na przykład jeśli były katalogów projektu C:\X, C:\Y i C:\Z z plików SBR w ich i chcesz, aby połączyć je wszystkie w jednym pliku .bsc, użyj BSCMAKE C:\X\\*.sbr C:\Y\\\*.sbr C:\Z\\\*. SBR /o c:\whatever_directory\combined.bsc do tworzenia pliku BSC połączone.  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia kompilacji C/C++](../../build/reference/c-cpp-build-tools.md)   
 [BSCMAKE — dokumentacja](../../build/reference/bscmake-reference.md)