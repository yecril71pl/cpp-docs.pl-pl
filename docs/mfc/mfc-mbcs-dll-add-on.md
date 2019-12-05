---
title: Dodatek MFC MBCS DLL Add-on
ms.date: 12/02/2019
helpviewer_keywords:
- MBCS
- MFC
ms.openlocfilehash: fe74e0639664b6a6a86a4c3269f174de441002f4
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810373"
---
# <a name="mfc-mbcs-dll-add-on"></a>Dodatek MFC MBCS DLL Add-on

Obsługa biblioteki MFC i jej bibliotek zestawów znaków wielobajtowych (MBCS) wymaga dodatkowego kroku podczas instalacji programu Visual Studio w Visual Studio 2013 i nowszych.

**Visual Studio 2013**: Domyślnie biblioteki MFC zainstalowane w programie Visual Studio 2013 obsługują tylko programowanie w formacie Unicode. Aby można było skompilować projekt MFC w Visual Studio 2013, który ma właściwość **zestawu znaków** ustawioną na **Używanie zestawu znaków wielobajtowych** lub **nie jest ustawiony**, potrzebne są biblioteki DLL MBCS. Pobierz bibliotekę DLL w [bibliotece MFC wielobajtowej dla Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=40770).

**Visual Studio 2015**: w składnikach Instalatora wizualizacji C++ są zawarte zarówno biblioteki DLL w formacie Unicode, jak i MBCS MFC, ale obsługa MFC nie jest instalowana domyślnie. Wizualizacje C++ i MFC są opcjonalnymi konfiguracjami instalacji w Instalatorze programu Visual Studio. Aby upewnić się, że biblioteka MFC jest zainstalowana, wybierz pozycję **niestandardowe** w instalatorze i w obszarze **Języki programowania**upewnij się, że wybrano  **C++ wizualizację** i **Microsoft Foundation Classes C++**  . Jeśli zainstalowano już program Visual Studio, podczas próby utworzenia projektu MFC zostanie C++ wyświetlony monit o zainstalowanie wizualizacji i/lub MFC.

**Visual Studio 2017 i nowsze**: biblioteki MFC w formacie Unicode i MBCS są instalowane z **programowaniem dla C++ komputerów stacjonarnych przy użyciu** obciążenia po wybraniu opcji **Obsługa MFC i ATL** z okienka **składniki opcjonalne** w programie Instalator programu Visual Studio. Jeśli instalacja nie obejmuje tych składników, przejdź do **pliku | Nowe projekty** okno dialogowe, a następnie kliknij link **Otwórz Instalator programu Visual Studio** . Aby uzyskać więcej informacji, zobacz [Instalowanie programu Visual Studio](/visualstudio/install/install-visual-studio).

## <a name="see-also"></a>Zobacz także

[Wersje biblioteki MFC](../mfc/mfc-library-versions.md)
