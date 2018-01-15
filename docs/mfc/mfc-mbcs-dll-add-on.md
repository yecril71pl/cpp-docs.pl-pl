---
title: MFC MBCS DLL dodatku | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 1/04/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MBCS
- MFC
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d6f134110ff95956cc37d6e038a680ff27cbc298
ms.sourcegitcommit: 56f6fce7d80e4f61d45752f4c8512e4ef0453e58
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2018
---
# <a name="mfc-mbcs-dll-add-on"></a>Dodatek MFC MBCS DLL Add-on

Obsługa MFC i bibliotek (MBCS) zestawu znaków wielobajtowych wymaga dodatkowych czynności podczas instalacji programu Visual Studio w programie Visual Studio 2013, 2015 i 2017 r.

**Visual Studio 2013**: domyślnie bibliotek MFC, zainstalowanych w programie Visual Studio 2013 obsługuje tylko programowanie Unicode. Niezbędną do kompilacji projektu programu Visual Studio 2013, która ma MFC MBCS dll **zestaw znaków** ustawioną właściwość **zestaw znaków wielobajtowego użyj** lub **Nieustawione**. Pobierz biblioteki DLL w [biblioteki MFC wielobajtowe dla programu Visual Studio 2013](https://www.microsoft.com/en-us/download/details.aspx?id=40770).

**Visual Studio 2015**: zarówno Unicode i biblioteki DLL MFC MBCS znajdują się w składników instalacji programu Visual C++, ale obsługa MFC nie jest instalowany domyślnie. Visual C++ i MFC to konfiguracje opcjonalne instalacji w Instalatorze programu Visual Studio. Aby upewnić się, że zainstalowano MFC, wybierz **niestandardowy** w konfiguracji i w obszarze **języki programowania**, upewnij się, że **Visual C++** i **Microsoft Foundation Classes dla języka C++** są wybrane. Jeśli zainstalowano program Visual Studio pojawi się monit do zainstalowania programu Visual C++ i/lub MFC podczas próby utworzenia projektu MFC.

**Visual Studio 2017**: Unicode i biblioteki DLL MFC MBCS są instalowane z **tworzenia klasycznych aplikacji w języku C++** obciążenia po wybraniu **MFC i ATL obsługuje** z  **Opcjonalne składniki** okienka. Jeśli instalacja nie zawiera tych składników, możesz uruchomić Instalatora z **nowe projekty** okna dialogowego za pomocą **Otwórz Instalator programu Visual Studio** łącza.

## <a name="see-also"></a>Zobacz także

[Wersje biblioteki MFC](../mfc/mfc-library-versions.md)

