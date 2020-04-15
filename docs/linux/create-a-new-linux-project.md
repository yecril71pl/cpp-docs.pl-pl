---
title: Tworzenie nowego projektu systemu Linux w języku C++ w programie Visual Studio
ms.date: 10/24/2019
description: Utwórz nowy projekt systemu Linux oparty na systemie MSBuild w programie Visual Studio.
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
ms.openlocfilehash: 1e79dd50756b71aabae7ccec75e57178898e7720
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364351"
---
# <a name="create-a-new-linux-project"></a>Tworzenie nowego projektu systemu Linux

::: moniker range="vs-2015"

Projekty systemu Linux są dostępne w programie Visual Studio 2017 i nowszych.

::: moniker-end

::: moniker range="vs-2017"

Najpierw upewnij się, że masz zainstalowane **obciążenie programistyczne systemu Linux** dla programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Pobieranie, instalowanie i konfigurowanie obciążenia systemu Linux](download-install-and-setup-the-linux-development-workload.md).

W przypadku kompilacji między platformami zaleca się użycie CMake. CMake wsparcie jest bardziej kompletne w programie Visual Studio 2019. Jeśli CMake nie jest opcją i masz istniejące rozwiązanie programu Windows Visual Studio, które chcesz rozszerzyć do kompilacji dla systemu Linux, można dodać projekt Visual Studio Linux do rozwiązania systemu Windows, wraz z projektem **elementy udostępnione.** Umieść kod, który jest współużytkowany między obiema platformami w projekcie Elementy udostępnione i dodaj odwołanie do tego projektu z projektów systemu Windows i Linux.

## <a name="to-create-a-new-linux-project"></a>Aby utworzyć nowy projekt systemu Linux

Aby utworzyć nowy projekt systemu Linux w programie Visual Studio 2017, wykonaj następujące kroki:

1. Wybierz **opcję Plik > nowy projekt** w programie Visual Studio lub naciśnij **klawisze Ctrl + Shift + N**.
1. Wybierz **węzeł Visual C++ > Cross Platform > linux,** a następnie wybierz typ projektu do utworzenia. Wprowadź **nazwę** i **lokalizację**i wybierz przycisk **OK**.

   ![Nowy projekt Linuksa](media/newproject.png)

   | Typ projektu | Opis |
   | ------------ | --- |
   | **Miganie (Malina)**           | Projekt przeznaczony dla urządzenia Raspberry Pi z przykładowym kodem migającym diodą LED |
   | **Aplikacja konsoli (Linux)** | Projekt przeznaczony dla dowolnego komputera z systemem Linux, z przykładowym kodem, który wyprowadza tekst do konsoli |
   | **Pusty projekt (Linux)**       | Projekt przeznaczony dla dowolnego komputera z systemem Linux, bez przykładowego kodu |
   | **Projekt Makefile (Linux)**    | Projekt przeznaczony dla każdego komputera z systemem Linux, zbudowany przy użyciu standardowego systemu kompilacji Makefile |

## <a name="next-steps"></a>Następne kroki

[Konfigurowanie projektu systemu Linux](configure-a-linux-project.md)

::: moniker-end

::: moniker range="vs-2019"

Najpierw upewnij się, że masz zainstalowane **obciążenie programistyczne systemu Linux** dla programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Pobieranie, instalowanie i konfigurowanie obciążenia systemu Linux](download-install-and-setup-the-linux-development-workload.md).

Podczas tworzenia nowego projektu C++ dla systemu Linux w programie Visual Studio, można utworzyć projekt programu Visual Studio lub projektu CMake. W tym artykule opisano sposób tworzenia projektu programu Visual Studio. Ogólnie rzecz biorąc dla nowych projektów, które mogą zawierać kod open source lub które zamierzasz skompilować do tworzenia między platformami, zaleca się użycie CMake z programem Visual Studio. Z projektu CMake można tworzyć i debugować ten sam projekt w systemie Windows i Linux. Aby uzyskać więcej informacji, zobacz [Tworzenie i konfigurowanie projektu CMake systemu Linux](cmake-linux-project.md).

Jeśli masz istniejące rozwiązanie programu Windows Visual Studio, które chcesz rozszerzyć do kompilacji dla systemu Linux, a CMake nie jest opcją, następnie można dodać projekt Visual Studio Linux do rozwiązania systemu Windows, wraz z projektem **elementy udostępnione.** Umieść kod, który jest współużytkowany między obiema platformami w projekcie Elementy udostępnione i dodaj odwołanie do tego projektu z projektów systemu Windows i Linux.

## <a name="to-create-a-new-linux-project"></a>Aby utworzyć nowy projekt systemu Linux

Aby utworzyć nowy projekt systemu Linux w programie Visual Studio 2019, wykonaj następujące kroki:

1. Wybierz **opcję Plik > nowy projekt** w programie Visual Studio lub naciśnij **klawisze Ctrl + Shift + N**.
1. Ustaw **język** na **C++** i wyszukaj "Linux". Wybierz typ projektu do utworzenia, a następnie wybierz pozycję **Dalej**. Wprowadź **nazwę** i **lokalizację**, a następnie wybierz pozycję **Utwórz**.

   ![Nowy projekt Linuksa](media/newproject-vs2019.png)

   | Typ projektu | Opis |
   | ------------ | --- |
   | **Miganie (Malina)**           | Projekt przeznaczony dla urządzenia Raspberry Pi z przykładowym kodem migającym diodą LED |
   | **Aplikacja konsoli (Linux)** | Projekt przeznaczony dla dowolnego komputera z systemem Linux, z przykładowym kodem, który wyprowadza tekst do konsoli |
   | **Pusty projekt (Linux)**       | Projekt przeznaczony dla dowolnego komputera z systemem Linux, bez przykładowego kodu |
   | **Projekt Makefile (Linux)**    | Projekt przeznaczony dla każdego komputera z systemem Linux, zbudowany przy użyciu standardowego systemu kompilacji Makefile |

## <a name="next-steps"></a>Następne kroki

[Konfigurowanie projektu systemu Linux](configure-a-linux-project.md)

::: moniker-end
