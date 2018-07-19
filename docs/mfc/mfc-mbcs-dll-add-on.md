---
title: Dodatek MFC MBCS DLL | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: aa6840fe54478b88e201dd09950917b95c7a1cc4
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/13/2018
ms.locfileid: "39025737"
---
# <a name="mfc-mbcs-dll-add-on"></a>Dodatek MFC MBCS DLL Add-on

Obsługa MFC i jego wielobajtowym zestawem (znaków MBCS) biblioteki wymaga dodatkowych czynności podczas instalowania programu Visual Studio w Visual Studio 2013, 2015 i 2017.

**Visual Studio 2013**: Domyślnie biblioteki MFC, zainstalowane w programie Visual Studio 2013 obsługuje tylko programowania Unicode. Pliki dll MBCS jest niezbędna, aby skompilować projekt MFC w Visual Studio 2013, która ma **zestaw znaków** właściwością **zestaw znaków wielobajtowych użyj** lub **Nieustawione**. Pobierz biblioteki DLL w [Multibyte MFC Library for Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=40770).

**Program Visual Studio 2015**: zarówno Unicode i MBCS MFC z biblioteki DLL są zawarte w składników instalacji programu Visual C++, ale obsługa MFC nie jest instalowany domyślnie. Visual C++ i MFC są konfiguracje opcjonalne instalacji w Instalatorze programu Visual Studio. Aby upewnić się, że zainstalowano MFC, wybierz **niestandardowe** w konfiguracji i w obszarze **języków programowania**, upewnij się, że **Visual C++** i **Microsoft Foundation Classes dla języka C++** są zaznaczone. Jeśli zainstalowano już program Visual Studio, monit będzie zainstalować Visual C++ i/lub MFC, podczas próby utworzenia projektu MFC.

**Program Visual Studio 2017**: Unicode i MBCS MFC dll, które są instalowane z **programowanie aplikacji klasycznych w języku C++** obciążenia po wybraniu **obsługuje MFC i ATL** z **opcjonalne Składniki** okienka. Jeśli instalacja nie zawiera tych składników, przejdź do **pliku | Nowe projekty** okno dialogowe i kliknij przycisk **Otwórz Instalator programu Visual Studio** łącza.

## <a name="see-also"></a>Zobacz także

[Wersje biblioteki MFC](../mfc/mfc-library-versions.md)

