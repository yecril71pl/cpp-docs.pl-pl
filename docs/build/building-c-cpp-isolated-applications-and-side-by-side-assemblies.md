---
title: Kompilowanie aplikacji izolowanych C/C++ oraz aplikacji wykonywanych równocześnie
ms.date: 05/06/2019
helpviewer_keywords:
- isolated applications [C++]
- WinSxS [C++]
- native assembly cache [C++]
- builds [C++], isolated applications
- side-by-side applications [C++]
- builds [C++], side-by-side assemblies
ms.assetid: 9465904e-76f7-48bd-bb3f-c55d8f1699b6
ms.openlocfilehash: b7deb68a441d392464dad8763f80bd4d9cdfcb17
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493355"
---
# <a name="building-cc-isolated-applications-and-side-by-side-assemblies"></a>Kompilowanie aplikacji izolowanych C/C++ oraz aplikacji wykonywanych równocześnie

Program Visual Studio obsługuje model wdrażania dla aplikacji klienckich systemu Windows oparty na koncepcji [izolowanych aplikacji](/windows/win32/SbsCs/isolated-applications) i [zestawów równoległych](/windows/win32/SbsCs/about-side-by-side-assemblies-). Domyślnie program Visual Studio kompiluje wszystkie natywne aplikacjeC++ C/w postaci aplikacji izolowanych, które używają manifestów do opisywania zależności od bibliotek wizualnych. [](/windows/win32/sbscs/manifests) C++

Kompilowanie CC++ /programów jako aplikacji izolowanych przedstawia szereg zalet. Na przykład aplikacja izolowana nie ma zastosowania, gdy inne C/C++ aplikacje instalują lub odinstalują biblioteki wizualne C++ . Biblioteki C++ wizualne używane przez aplikacje izolowane mogą być nadal rozpowszechniane w folderze lokalnym aplikacji lub przez instalację do natywnej pamięci podręcznej zestawów (winsxs); jednak obsługa bibliotek wizualnych C++ dla już wdrożonych aplikacji może być uproszczona przy użyciu [pliku konfiguracji wydawcy](/windows/win32/SbsCs/publisher-configuration). Model wdrażania izolowanych aplikacji ułatwia upewnienie się, że aplikacje CC++ /uruchomione na określonym komputerze używają najnowszej wersji bibliotek wizualnych C++ , pozostawiając jednocześnie możliwość otwarcia systemu Administratorzy i autorzy aplikacji, aby kontrolować jawne powiązanie wersji aplikacji z ich zależnymi bibliotekami DLL.

W tej sekcji omówiono, jak można skompilować aplikację CC++ /aplikacje jako izolowaną aplikację i upewnić się, że jest C++ ona powiązana z bibliotekami wizualnymi przy użyciu manifestu. Informacje zawarte w tej sekcji dotyczą głównie natywnych lub niezarządzanych C++ aplikacji. Aby uzyskać informacje o wdrażaniu aplikacji natywnych C++ skompilowanych za pomocą programu Visual Studio, zobacz Redystrybuowanie [plików wizualnych C++ ](../windows/redistributing-visual-cpp-files.md).

## <a name="in-this-section"></a>W tej sekcji

[Pojęcia związane z aplikacjami izolowanymi oraz aplikacjami wykonywanymi równocześnie](concepts-of-isolated-applications-and-side-by-side-assemblies.md)

[Kompilowanie izolowanych aplikacji C/C++](building-c-cpp-isolated-applications.md)

[Kompilowanie wykonywanych jednocześnie aplikacji C/C++](building-c-cpp-side-by-side-assemblies.md)

[Instrukcje: kompilowanie komponentów COM bez rejestrowania](how-to-build-registration-free-com-components.md)

[Instrukcje: kompilowanie izolowanych aplikacji korzystających ze składników COM](how-to-build-isolated-applications-to-consume-com-components.md)

[Ogólne informacje o tworzeniu manifestu dla programów C/C++](understanding-manifest-generation-for-c-cpp-programs.md)

[Rozwiązywanie problemów związanych z aplikacjami izolowanymi C/C++ oraz aplikacjami wykonywanymi równocześnie](troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)

## <a name="related-sections"></a>Sekcje pokrewne

[Aplikacje izolowane i zestawy równoległe](/windows/win32/SbsCs/isolated-applications-and-side-by-side-assemblies-portal)

[Wdrażanie aplikacji klasycznych](../windows/deploying-native-desktop-applications-visual-cpp.md)