---
title: Tworzenie projektu systemu Linux MSBuild C++ w programie Visual Studio
ms.date: 08/04/2020
description: Utwórz nowy projekt systemu Linux oparty na programie MSBuild w programie Visual Studio.
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
ms.openlocfilehash: 86d8b8fd2abe8970b5146d4ab08dc4251b5562d5
ms.sourcegitcommit: 2034f8e744a8b36cff8b15e9a5cfe684afebadfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2020
ms.locfileid: "88043853"
---
# <a name="create-a-linux-msbuild-c-project-in-visual-studio"></a>Tworzenie projektu systemu Linux MSBuild C++ w programie Visual Studio

::: moniker range="vs-2015"

Projekty systemu Linux są dostępne w programie Visual Studio 2017 i nowszych.

::: moniker-end

::: moniker range="vs-2017"

Najpierw upewnij się, że masz zainstalowane **obciążenie deweloperskie systemu Linux** dla programu Visual Studio. Aby uzyskać więcej informacji, zobacz [pobieranie, Instalowanie i Konfigurowanie obciążenia systemu Linux](download-install-and-setup-the-linux-development-workload.md).

W przypadku kompilacji na wielu platformach zalecamy użycie CMake. Obsługa CMake jest bardziej kompletna w programie Visual Studio 2019. Jeśli CMake nie jest opcją i masz istniejące rozwiązanie Windows Visual Studio, które ma zostać rozbudowane do kompilacji dla systemu Linux, możesz dodać projekt programu Visual Studio Linux do rozwiązania systemu Windows wraz z projektem **elementów współużytkowanych** . Umieść kod, który jest współużytkowany między obiema platformami w projekcie elementy udostępnione, i Dodaj odwołanie do tego projektu z projektów systemu Windows i Linux.

## <a name="to-create-a-new-linux-project"></a>Aby utworzyć nowy projekt systemu Linux

Aby utworzyć nowy projekt systemu Linux w programie Visual Studio 2017, wykonaj następujące kroki:

1. Wybierz pozycję **plik > nowy projekt** w programie Visual Studio lub naciśnij **klawisze Ctrl + Shift + N**.
1. Wybierz węzeł **Visual C++ > wielu Platform > Linux** , a następnie wybierz typ projektu do utworzenia. Wprowadź **nazwę** i **lokalizację**, a następnie wybierz **przycisk OK**.

   ![Nowy projekt systemu Linux](media/newproject.png)

   | Typ projektu | Opis |
   | ------------ | --- |
   | **Miganie (Raspberry)**           | Projekt przeznaczony dla urządzenia Raspberry Pi z przykładowym kodem, który miga diody LED |
   | **Aplikacja konsolowa (Linux)** | Projekt przeznaczony dla dowolnego komputera z systemem Linux z przykładowym kodem, który wyprowadza tekst do konsoli |
   | **Pusty projekt (Linux)**       | Projekt przeznaczony dla dowolnego komputera z systemem Linux bez przykładowego kodu |
   | **Projekt pliku reguł programu make (Linux)**    | Projekt przeznaczony dla dowolnego komputera z systemem Linux utworzony przy użyciu standardowego systemu kompilacji pliku reguł programu make |

## <a name="next-steps"></a>Następne kroki

[Konfigurowanie projektu programu MSBuild dla systemu Linux](configure-a-linux-project.md)

::: moniker-end

::: moniker range="vs-2019"

Najpierw upewnij się, że masz zainstalowane **obciążenie deweloperskie systemu Linux** dla programu Visual Studio. Aby uzyskać więcej informacji, zobacz [pobieranie, Instalowanie i Konfigurowanie obciążenia systemu Linux](download-install-and-setup-the-linux-development-workload.md).

Podczas tworzenia nowego projektu C++ dla systemu Linux w programie Visual Studio można utworzyć projekt programu Visual Studio lub projekt CMake. W tym artykule opisano sposób tworzenia projektu programu Visual Studio. Ogólnie rzecz biorąc, w przypadku nowych projektów, które mogą obejmować kod w języku Open Source lub który ma zostać skompilowany do opracowania na wiele platform, zalecamy użycie CMake z programem Visual Studio. Za pomocą projektu CMake można kompilować i debugować ten sam projekt zarówno w systemie Windows, jak i Linux. Aby uzyskać więcej informacji, zobacz [Tworzenie i Konfigurowanie projektu systemu Linux CMAKE](cmake-linux-project.md).

Jeśli masz istniejące rozwiązanie Windows Visual Studio, które chcesz rozłożyć na kompilację dla systemu Linux, a CMake nie jest opcją, możesz dodać projekt programu Visual Studio Linux do rozwiązania systemu Windows wraz z projektem **elementów współużytkowanych** . Umieść kod, który jest współużytkowany między obiema platformami w projekcie elementy udostępnione, i Dodaj odwołanie do tego projektu z projektów systemu Windows i Linux.

## <a name="to-create-a-new-linux-project"></a>Aby utworzyć nowy projekt systemu Linux

Aby utworzyć nowy projekt systemu Linux w programie Visual Studio 2019, wykonaj następujące kroki:

1. Wybierz pozycję **plik > nowy projekt** w programie Visual Studio lub naciśnij **klawisze Ctrl + Shift + N**.
1. Ustaw **Język** **C++** i wyszukaj ciąg "Linux". Wybierz typ projektu, który chcesz utworzyć, a następnie wybierz przycisk **dalej**. Wprowadź **nazwę** i **lokalizację**, a następnie wybierz pozycję **Utwórz**.

   ![Nowy projekt systemu Linux](media/newproject-vs2019.png)

   | Typ projektu | Opis |
   | ------------ | --- |
   | **Miganie (Raspberry)**           | Projekt przeznaczony dla urządzenia Raspberry Pi z przykładowym kodem, który miga diody LED |
   | **Aplikacja konsolowa (Linux)** | Projekt przeznaczony dla dowolnego komputera z systemem Linux z przykładowym kodem, który wyprowadza tekst do konsoli |
   | **Pusty projekt (Linux)**       | Projekt przeznaczony dla dowolnego komputera z systemem Linux bez przykładowego kodu |
   | **Projekt pliku reguł programu make (Linux)**    | Projekt przeznaczony dla dowolnego komputera z systemem Linux utworzony przy użyciu standardowego systemu kompilacji pliku reguł programu make |

## <a name="next-steps"></a>Następne kroki

[Konfigurowanie projektu programu MSBuild dla systemu Linux](configure-a-linux-project.md)

::: moniker-end
