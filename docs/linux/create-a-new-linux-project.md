---
title: Tworzenie nowego projektu systemu Linux w języku C++ w programie Visual Studio
ms.date: 09/12/2018
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
ms.openlocfilehash: bd5ab1d2bc1077f366082bf8767f8f690173ac8b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393198"
---
# <a name="create-a-new-linux-project"></a>Tworzenie nowego projektu systemu Linux

Najpierw upewnij się, że masz **obciążenia projektowanie systemu Linux** dla zainstalowanego programu Visual Studio. Aby uzyskać więcej informacji, zobacz [pobieranie, instalowanie i konfigurowanie obciążenia Linux](download-install-and-setup-the-linux-development-workload.md).

Podczas tworzenia nowego projektu w języku C++ w programie Visual Studio dla systemu Linux, masz możliwość tworzenia projektu programu Visual Studio lub projektu narzędzia CMake. W tym temacie opisano sposób tworzenia projektu programu Visual Studio. Aby uzyskać informacji na temat tworzenia i pracy z istniejących projektów CMake, zobacz [Konfigurowanie projektu CMake systemu Linux ](cmake-linux-project.md).

Aby utworzyć nowego projektu systemu Linux w programie Visual Studio, wykonaj następujące czynności:

1. Wybierz **Plik > Nowy projekt** w programie Visual Studio lub naciśnij klawisz **Ctrl + Shift + N**.
1. Wybierz **Visual C++ > wiele Platform > Linux** węzeł, a następnie wybierz typ projektu chcesz utworzyć, wprowadź nazwę/lokalizację i kliknij przycisk OK.

   ![Nowego projektu systemu Linux](media/newproject.png)

   | Typ projektu | Opis
   | ------------ | ---
   | **Miganie (Raspberry)**           | Projekt przeznaczony dla urządzenia Raspberry Pi z przykładowym kodem zapisywane blink diody LED
   | **Aplikacja konsoli (Linux)** | Projekt przeznaczony dla dowolnego komputera z systemem Linux przy użyciu przykładowy kod napisany w danych wyjściowych tekst do konsoli
   | **Pusty projekt (Linux)**       | Docelowe dowolnego komputera z systemem Linux przy użyciu nie przykładowy kod napisany projektu
   | **Projekt pliku reguł programu make (Linux)**    | Projekt przeznaczony dla dowolnego komputera z systemem Linux, która zostanie utworzona przy użyciu standardowego pliku reguł programu make systemu kompilacji
