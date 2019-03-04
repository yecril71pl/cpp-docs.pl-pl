---
title: Dodatek MFC MBCS DLL Add-on
ms.date: 1/04/2018
helpviewer_keywords:
- MBCS
- MFC
ms.openlocfilehash: 2fdbb5dd862c7d1a8845813c6234fea9e902c1f9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57292506"
---
# <a name="mfc-mbcs-dll-add-on"></a>Dodatek MFC MBCS DLL Add-on

Obsługa MFC i jego wielobajtowym zestawem (znaków MBCS) biblioteki wymaga dodatkowych czynności podczas instalowania programu Visual Studio w Visual Studio 2013, 2015 i 2017.

**Visual Studio 2013**: Domyślnie biblioteki MFC, zainstalowane w programie Visual Studio 2013 obsługuje tylko programowania Unicode. Pliki dll MBCS jest niezbędna, aby skompilować projekt MFC w Visual Studio 2013, która ma **zestaw znaków** właściwością **zestaw znaków wielobajtowych użyj** lub **Nieustawione**. Pobierz biblioteki DLL w [Multibyte MFC Library for Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=40770).

**Visual Studio 2015**: Unicode i MBCS MFC z biblioteki DLL są objęte składników instalacji programu Visual C++, ale obsługa MFC nie jest instalowany domyślnie. Visual C++ i MFC są konfiguracje opcjonalne instalacji w Instalatorze programu Visual Studio. Aby upewnić się, że zainstalowano MFC, wybierz **niestandardowe** w konfiguracji i w obszarze **języków programowania**, upewnij się, że **Visual C++** i **Microsoft Foundation Classes dla języka C++** są zaznaczone. Jeśli zainstalowano już program Visual Studio, monit będzie zainstalować Visual C++ i/lub MFC, podczas próby utworzenia projektu MFC.

**Visual Studio 2017**: Unicode i MBCS MFC dll, które są instalowane z **programowanie aplikacji klasycznych w języku C++** obciążenia po wybraniu **obsługuje MFC i ATL** z **składniki opcjonalne** okienka. Jeśli instalacja nie zawiera tych składników, przejdź do **pliku | Nowe projekty** okno dialogowe i kliknij przycisk **Otwórz Instalator programu Visual Studio** łącza.

## <a name="see-also"></a>Zobacz także

[Wersje biblioteki MFC](../mfc/mfc-library-versions.md)
