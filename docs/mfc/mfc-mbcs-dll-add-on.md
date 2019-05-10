---
title: Dodatek MFC MBCS DLL Add-on
ms.date: 05/08/2019
helpviewer_keywords:
- MBCS
- MFC
ms.openlocfilehash: 20145b200a0f8bac8ccb461331d4d233a3b0251e
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524817"
---
# <a name="mfc-mbcs-dll-add-on"></a>Dodatek MFC MBCS DLL Add-on

Obsługa MFC i jego wielobajtowym zestawem (znaków MBCS) biblioteki wymaga dodatkowych czynności podczas instalowania programu Visual Studio w programie Visual Studio 2013 lub nowszy.

**Visual Studio 2013**: Domyślnie biblioteki MFC, zainstalowane w programie Visual Studio 2013 obsługuje tylko programowania Unicode. Pliki dll MBCS jest niezbędna, aby skompilować projekt MFC w Visual Studio 2013, która ma **zestaw znaków** właściwością **zestaw znaków wielobajtowych użyj** lub **Nieustawione**. Pobierz biblioteki DLL w [Multibyte MFC Library for Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=40770).

**Visual Studio 2015**: Unicode i MBCS MFC z biblioteki DLL są objęte składników instalacji programu Visual C++, ale obsługa MFC nie jest instalowany domyślnie. Visual C++ i MFC są konfiguracje opcjonalne instalacji w Instalatorze programu Visual Studio. Aby upewnić się, że zainstalowano MFC, wybierz **niestandardowe** w konfiguracji i w obszarze **języków programowania**, upewnij się, że **Visual C++** i **Microsoft Foundation Classes dla języka C++** są zaznaczone. Jeśli zainstalowano już program Visual Studio, monit będzie zainstalować Visual C++ i/lub MFC, podczas próby utworzenia projektu MFC.

**Visual Studio 2017 i nowszym**: Unicode i MBCS MFC dll, które są instalowane z **programowanie aplikacji klasycznych w języku C++** obciążenia po wybraniu **obsługuje MFC i ATL** z **składniki opcjonalne** okienka. Jeśli instalacja nie zawiera tych składników, przejdź do **pliku | Nowe projekty** okno dialogowe i kliknij przycisk **Otwórz Instalator programu Visual Studio** łącza.

## <a name="see-also"></a>Zobacz także

[Wersje biblioteki MFC](../mfc/mfc-library-versions.md)
