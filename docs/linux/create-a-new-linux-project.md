---
title: Tworzenie nowego projektu systemu Linux w języku C++ w programie Visual Studio
ms.date: 06/11/2019
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
ms.openlocfilehash: 0377e21177b29d998fc3e66bb1863dbc127c1fbe
ms.sourcegitcommit: fde637f823494532314790602c2819f889706ff6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2019
ms.locfileid: "67042708"
---
# <a name="create-a-new-linux-project"></a>Tworzenie nowego projektu systemu Linux

::: moniker range="vs-2015"

Projektów systemu Linux są dostępne w programie Visual Studio 2017 i nowszych wersjach.

::: moniker-end

Najpierw upewnij się, że masz **obciążenia projektowanie systemu Linux** dla zainstalowanego programu Visual Studio. Aby uzyskać więcej informacji, zobacz [pobieranie, instalowanie i konfigurowanie obciążenia Linux](download-install-and-setup-the-linux-development-workload.md).

Podczas tworzenia nowego C++ projektu dla systemu Linux w programie Visual Studio, można wybrać utworzyć projekt programu Visual Studio lub projektu narzędzia CMake. W tym artykule opisano sposób tworzenia projektu programu Visual Studio. Aby uzyskać informacje o sposobie tworzenia i pracy z istniejących projektów CMake, zobacz [tworzenie i konfigurowanie projektu CMake systemu Linux ](cmake-linux-project.md).

## <a name="to-create-a-new-linux-project"></a>Aby utworzyć nowy projekt systemu Linux

Aby utworzyć nowego projektu systemu Linux w programie Visual Studio, wykonaj następujące kroki:

::: moniker range="vs-2019"

1. Wybierz **Plik > Nowy projekt** w programie Visual Studio lub naciśnij klawisz **Ctrl + Shift + N**.
1. Ustaw **języka** do **C++** i poszukaj pozycji "Linux". Wybierz typ projektu, aby utworzyć, a następnie wybierz **dalej**. Wprowadź **nazwa** i **lokalizacji**i wybierz polecenie **Utwórz**.

   ![Nowego projektu systemu Linux](media/newproject-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

1. Wybierz **Plik > Nowy projekt** w programie Visual Studio lub naciśnij klawisz **Ctrl + Shift + N**.
1. Wybierz **Visual C++ > wiele Platform > Linux** węzeł, a następnie wybierz typ projektu do utworzenia. Wprowadź **nazwa** i **lokalizacji**i wybierz polecenie **OK**.

   ![Nowego projektu systemu Linux](media/newproject.png)

::: moniker-end

   | Typ projektu | Opis |
   | ------------ | --- |
   | **Miganie (Raspberry)**           | Projekt przeznaczony dla urządzenia Raspberry Pi, przy użyciu przykładowy kod, który miga diody LED |
   | **Aplikacja konsoli (Linux)** | Projekt przeznaczony dla dowolnego komputera z systemem Linux, przykładowy kod, który wyświetla tekst do konsoli |
   | **Pusty projekt (Linux)**       | Projekt przeznaczony dla dowolnego komputera z systemem Linux, nie przykładowy kod |
   | **Projekt pliku reguł programu make (Linux)**    | Projekt przeznaczony dla dowolnego komputera z systemem Linux utworzone przy użyciu standardowego pliku reguł programu make systemu kompilacji |

   ::: moniker range="vs-2019"

   Visual Studio 2019 umożliwia utworzenie nowego projektu narzędzia CMake. Aby uzyskać więcej informacji, zobacz [tworzenie i konfigurowanie projektu CMake systemu Linux ](cmake-linux-project.md).
   
   ::: moniker-end

## <a name="next-steps"></a>Następne kroki

[Konfigurowanie projektu systemu Linux](configure-a-linux-project.md)
