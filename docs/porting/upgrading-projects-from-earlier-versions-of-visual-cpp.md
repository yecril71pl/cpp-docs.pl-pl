---
title: Uaktualnianie projektów ze starszych wersji programu Visual C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- 32-bit code porting
- upgrading Visual C++ applications, 32-bit code
ms.assetid: 18cdacaa-4742-43db-9e4c-2d9e73d8cc84
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c503a2feae728c67507bf80db6eb2c5dabc3252f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33849733"
---
# <a name="upgrading-projects-from-earlier-versions-of-visual-c"></a>Uaktualnianie projektów ze starszych wersji programu Visual C++
W większości przypadków można otworzyć projektu, który został utworzony we wcześniejszej wersji programu Visual Studio. Jednak w takim przypadku Visual Studio uaktualnia projekt. Jeśli zapiszesz uaktualniony projekt, nie będzie go można otworzyć w starszej wersji.  
  
> [!IMPORTANT]
>  Jeśli próbujesz konwertować projekt, który został już przekonwertowany, Visual Studio wyświetla prośbę o potwierdzenie, ponieważ ponowna konwersja usuwa istniejące pliki.  
  
 Wiele uaktualnionych projektów i rozwiązań można skompilować bez modyfikacji. Jednak niektóre projekty mogą wymagać zmian ustawień i/lub kodu źródłowego. Warto się posłużyć następującymi wytycznymi, aby najpierw rozwiązać problemy z ustawieniami, a potem, jeśli projektu dalej nie da się skompilować, można rozwiązać problemy z kodem. Aby uzyskać więcej informacji, zobacz [omówienie potencjalne problemy z uaktualnieniem](../porting/overview-of-potential-upgrade-issues-visual-cpp.md).  
  
1.  Utwórz kopię istniejących plików projektu i rozwiązania. Zainstaluj aktualną wersję Visual Studio i starszą wersję obok siebie, tak aby w razie potrzeby można było porównać wersje plików.  
  
2.  W aktualnej wersji Visual Studio, otwórz — a tym samym uaktualnij — kopię projektu lub rozwiązania i zapisz ją.  
  
3.  Dla każdego projektu przekonwertowany, otwórz menu skrótów i wybierz polecenie **właściwości**. W obszarze **właściwości konfiguracji**, wybierz pozycję **ogólne** , a następnie dla **zestaw narzędzi platformy**, wybierz bieżącą wersję. (Na przykład dla programu Visual Studio 2017 r, wybierz pozycję v141.)  
  
4.  Skompiluj rozwiązanie. Jeżeli kompilacja zakończy się niepowodzeniem, zmodyfikuj ustawienia i zrekompiluj.  
  
 Źródła danych są zawarte w oddzielnym projekcie bazy danych, tak że można łatwo modyfikować i debugować procedury zapisane w tych źródłach. W przypadku uaktualniania projektu C++, który zawiera źródła danych, automatycznie jest tworzony oddzielny projekt bazy danych.  
  
 Aby uzyskać informacje o sposobie aktualizowania docelowej wersji systemu Windows, zobacz [modyfikowanie WINVER i _WIN32_WINNT](../porting/modifying-winver-and-win32-winnt.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zmiany systemu kompilacji](../build/build-system-changes.md)  
 [Nowości w języku Visual C++ w programie Visual Studio 2017](../what-s-new-for-visual-cpp-in-visual-studio.md) [Historia 2003 2015 zmian Visual C++](../porting/visual-cpp-change-history-2003-2015.md)   
 [Niestandardowe zachowanie](../cpp/nonstandard-behavior.md)