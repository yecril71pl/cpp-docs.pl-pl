---
title: Tworzenie nowego projektu systemu Linux w języku C++ w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 07/20/2018
ms.technology:
- cpp-linux
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: f64f8eaf09e92df3dd776180db5904af039d6ad7
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39207973"
---
# <a name="create-a-new-linux-project"></a>Tworzenie nowego projektu systemu Linux
Podczas pisania kodu C++ w programie Visual Studio dla systemu Linux, masz możliwość tworzenia projektu programu Visual Studio lub projektu narzędzia CMake. W tym temacie opisano sposób tworzenia projektu programu Visual Studio. Aby uzyskać informacji na temat projektów CMake, zobacz [Konfigurowanie projektu CMake systemu Linux ](cmake-linux-project.md).

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

