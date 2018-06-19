---
title: Utwórz nowy projekt C++ Linux w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2017
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
ms.openlocfilehash: 4d4d11ec459215d81996d1daea420513c21b10b9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339232"
---
# <a name="create-a-new-linux-project"></a>Utwórz nowy projekt systemu Linux
Podczas pisania kodu dla systemu Linux, jest możliwe utworzenia projektu programu Visual Studio lub CMake projektu. W tym temacie opisano sposób tworzenia projektu programu Visual Studio. Informacje dla projektów CMake, zobacz [Konfigurowanie projektu CMake Linux ](cmake-linux-project.md).

Aby utworzyć nowy projekt systemu Linux w programie Visual Studio, wykonaj następujące czynności:

1. Wybierz **Plik > Nowy projekt** w programie Visual Studio lub naciśnij klawisz **Ctrl + Shift + N**.
1. Wybierz **Visual C++ > Cross Platform > Linux** węzeł, a następnie wybierz typ projektu chcesz utworzyć, wprowadź nazwę/lokalizację i kliknij przycisk OK.

   ![Nowy projekt systemu Linux](media/newproject.png)

   | Typ projektu | Opis
   | ------------ | ---
   | **BLINK (malina)**           | Projekt przeznaczony dla urządzenia Pi malina z przykładowy kod napisany miga LED
   | **Aplikacja konsolowa (Linux)** | Projekt przeznaczony dla dowolnego komputera z systemem Linux z przykładowym kodzie zapisany do wyjścia tekstu do konsoli
   | **Pusty projekt (Linux)**       | Projekt przeznaczony dla dowolnego komputera Linux z nie przykładowy kod napisany
   | **Projektu pliku reguł programu make (Linux)**    | Projekt przeznaczony dla dowolnego komputera z systemem Linux, która zostanie utworzona przy użyciu standardowego pliku reguł programu make systemu kompilacji

