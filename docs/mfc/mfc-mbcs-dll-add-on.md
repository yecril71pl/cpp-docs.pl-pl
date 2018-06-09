---
title: MFC MBCS DLL dodatku | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 1/04/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MBCS
- MFC
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: efcfac98c5ff36f84ec0b7c4d2fbd6ff40cbb0d4
ms.sourcegitcommit: 59afc95d0e494af658cf464503f7f89bd1a8d2ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2018
ms.locfileid: "35239453"
---
# <a name="mfc-mbcs-dll-add-on"></a>Dodatek MFC MBCS DLL Add-on

Obsługa MFC i bibliotek (MBCS) zestawu znaków wielobajtowych wymaga dodatkowych czynności podczas instalacji programu Visual Studio w programie Visual Studio 2013, 2015 i 2017 r.

**Visual Studio 2013**: domyślnie bibliotek MFC, zainstalowanych w programie Visual Studio 2013 obsługuje tylko programowanie Unicode. Niezbędną do kompilacji projektu programu Visual Studio 2013, która ma MFC MBCS dll **zestaw znaków** ustawioną właściwość **zestaw znaków wielobajtowego użyj** lub **Nieustawione**. Pobierz biblioteki DLL w [biblioteki MFC wielobajtowe dla programu Visual Studio 2013](https://www.microsoft.com/en-us/download/details.aspx?id=40770).

**Visual Studio 2015**: zarówno Unicode i biblioteki DLL MFC MBCS znajdują się w składników instalacji programu Visual C++, ale obsługa MFC nie jest instalowany domyślnie. Visual C++ i MFC to konfiguracje opcjonalne instalacji w Instalatorze programu Visual Studio. Aby upewnić się, że zainstalowano MFC, wybierz **niestandardowy** w konfiguracji i w obszarze **języki programowania**, upewnij się, że **Visual C++** i **Microsoft Foundation Classes dla języka C++** są wybrane. Jeśli zainstalowano program Visual Studio pojawi się monit do zainstalowania programu Visual C++ i/lub MFC podczas próby utworzenia projektu MFC.

**Visual Studio 2017**: Unicode i biblioteki DLL MFC MBCS są instalowane z **tworzenia klasycznych aplikacji w języku C++** obciążenia po wybraniu **MFC i ATL obsługuje** z **opcjonalne Składniki** okienka. Jeśli instalacja nie zawiera tych składników, przejdź do **pliku | Nowe projekty** okno dialogowe i kliknij przycisk **Otwórz Instalator programu Visual Studio** łącza.

## <a name="see-also"></a>Zobacz także

[Wersje biblioteki MFC](../mfc/mfc-library-versions.md)

