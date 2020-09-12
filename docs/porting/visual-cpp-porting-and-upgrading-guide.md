---
title: Przewodnik dotyczący przenoszenia i uaktualniania języka Microsoft C++
description: Uaktualnij program Microsoft C++ Code do najnowszej wersji programu Visual Studio.
ms.date: 09/10/2020
ms.assetid: f5fbcc3d-aa72-41a6-ad9a-a706af2166fb
ms.topic: overview
ms.openlocfilehash: b6cd3461ee16a44162fdb641170a2f05d9b77369
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039537"
---
# <a name="microsoft-c-porting-and-upgrading-guide"></a>Przewodnik dotyczący przenoszenia i uaktualniania języka Microsoft C++

Ten artykuł zawiera Przewodnik uaktualniania kodu Microsoft C++ do najnowszej wersji programu Visual Studio. W przypadku projektów utworzonych w programie Visual Studio 2010 do 2015, po prostu otwórz projekt w programie Visual Studio 2019. Możesz uaktualnić projekt programu Visual Studio 2008 lub starszego w dwóch krokach. Aby najpierw przekonwertować projekt na format MSBuild, użyj programu Visual Studio 2010. Następnie otwórz projekt w programie Visual Studio 2019. Aby uzyskać pełne instrukcje, zobacz [uaktualnianie projektów C++ z wcześniejszych wersji programu Visual Studio](upgrading-projects-from-earlier-versions-of-visual-cpp.md).

Zestawy narzędzi w programie Visual Studio 2015, Visual Studio 2017 i Visual Studio 2019 są zgodne ze standardem binarnym. Teraz można przeprowadzić uaktualnienie do nowszej wersji kompilatora bez konieczności uaktualniania zależności biblioteki. Aby uzyskać więcej informacji, zobacz [zgodność binarna języka C++ 2015-2019](binary-compat-2015-2017.md).

Podczas uaktualniania projektów korzystających z bibliotek typu open source lub przeznaczonych do uruchamiania na wielu platformach zaleca się przeprowadzenie migracji do projektu opartego na CMake. Aby uzyskać więcej informacji, zobacz [CMAKE projects in Visual Studio](../build/cmake-projects-in-visual-studio.md)

## <a name="reasons-to-upgrade-c-code"></a>Przyczyny uaktualnienia kodu C++

Jeśli Starsza aplikacja działa prawidłowo, w bezpiecznym środowisku i nie jest objęta aktywnym programowaniem, może się okazać, że nie ma dużo zachęty do jej uaktualnienia. Jednak w takich przypadkach należy rozważyć uaktualnienie: aplikacja wymaga trwającej konserwacji. Lub, wykonujesz nową funkcję, lub wprowadzasz ulepszenia dotyczące wydajności lub zabezpieczeń. Uaktualnienie oferuje następujące korzyści:

- Ten sam kod może działać szybciej, ponieważ udoskonalono optymalizacje kompilatora.

- Nowoczesne funkcje języka C++ i praktyki programistyczne eliminują wiele typowych przyczyn błędów i tworzą kod, który jest bardzo łatwiejszy do utrzymania niż starszy Idiomy w stylu języka C.

- Czasy kompilacji są szybsze z powodu ulepszeń wydajności w kompilatorze i konsolidatorze.

- Lepsza zgodność ze standardami. Opcja kompilatora [/permissive-](../build/reference/permissive-standards-conformance.md) pomaga identyfikować kod, który nie jest zgodny z bieżącym standardem języka C++. [Nowy preprocesor](../preprocessor/preprocessor-experimental-overview.md) obsługuje również zgodność kodu.

- Lepsza ochrona w czasie wykonywania, w tym bezpieczniejsze funkcje [biblioteki środowiska uruchomieniowego języka C](../c-runtime-library/security-features-in-the-crt.md) . Funkcje kompilatora, takie jak [Sprawdzanie osłony](../build/reference/guard-enable-guard-checks.md) i oczyszczanie adresów (Nowość w programie Visual Studio 2019 w wersji 16,4).

## <a name="multitargeting-vs-upgrading"></a>Wieloelementowe a uaktualnianie

Prawdopodobnie uaktualnienie bazy kodu do nowego zestawu narzędzi nie jest opcją dla Ciebie. Można nadal używać najnowszej wersji programu Visual Studio do tworzenia i edytowania projektów, które używają starszych zestawów narzędzi i bibliotek. W programie Visual Studio 2019 można korzystać z funkcji takich jak:

- nowoczesne, statyczne narzędzia analityczne, w tym podstawowe wytyczne dotyczące języka C++ sprawdzające i Clang-uporządkowanego, aby ułatwić identyfikację potencjalnych problemów w kodzie źródłowym.

- Automatyczne formatowanie zgodnie z wybranymi nowoczesnymi stylami może pomóc w zwiększeniu czytelności kodu w starszej wersji.

Aby uzyskać więcej informacji, zobacz [Używanie natywnego wielu elementów docelowych w programie Visual Studio do kompilowania starych projektów](use-native-multi-targeting.md).

## <a name="in-this-section"></a>W tej sekcji

|Tytuł|Opis|
|-----------|-----------------|
|[Uaktualnianie projektów C++ z wcześniejszych wersji programu Visual Studio](upgrading-projects-from-earlier-versions-of-visual-cpp.md)|Jak uaktualnić bazę kodu do programu Visual Studio 2019 i v142 kompilatora.|
|[Narzędzia IDE do uaktualniania kodu C++](ide-tools-for-upgrading-code.md)|Przydatne funkcje środowiska IDE, które pomagają w procesie uaktualniania.|
|[C++ — zgodność binarna 2015–2019](binary-compat-2015-2017.md)|Korzystaj z bibliotek wersji 140 i najnowsze 141, tak jak w przypadku projektów v142.|
|[Używanie natywnej wielowersyjności kodu w programie Visual Studio do kompilacji starych projektów](use-native-multi-targeting.md)|Użyj programu Visual Studio 2019 ze starszymi kompilatorami i bibliotekami.|
|[Visual C++ — historia zmian w latach 2003–2015](visual-cpp-change-history-2003-2015.md)|Lista wszystkich zmian w bibliotekach i narzędziach kompilacji języka Microsoft C++ z programu Visual Studio 2003 do 2015, które mogą wymagać zmian w kodzie.|
|[Visual C++ — co nowego od roku 2003 do 2015](visual-cpp-what-s-new-2003-through-2015.md)|Wszystkie informacje "co nowego" dotyczące programu Microsoft C++ z programu Visual Studio 2003 za pośrednictwem programu Visual Studio 2015.|
|[Przenoszenie i uaktualnianie: Przykłady i analizy przypadków](porting-and-upgrading-examples-and-case-studies.md)|W tej sekcji zostały przewoźny i uaktualniony kilka przykładów i aplikacji oraz omówione zostały środowiska i wyniki. Te artykuły zawierają informacje o tym, co obejmuje proces przenoszenia i uaktualniania. W trakcie całego procesu omówiono porady i wskazówki dotyczące uaktualniania oraz pokazujące, jak określone błędy zostały naprawione.|
|[Przenoszenie do platforma uniwersalna systemu Windows](porting-to-the-universal-windows-platform-cpp.md)|Zawiera informacje na temat przenoszenia kodu do systemu Windows 10|
|[Wprowadzenie do programu Visual C++ dla użytkowników systemu UNIX](introduction-to-visual-cpp-for-unix-users.md)|Zawiera informacje dla użytkowników systemu UNIX, którzy są nowym programem do Visual C++ i chcą pracować z nim.|
|[Uruchamianie programów systemu Linux w systemie Windows](porting-from-unix-to-win32.md)|W tym artykule omówiono opcje migrowania aplikacji systemu UNIX do systemu Windows.|

## <a name="see-also"></a>Zobacz także

[Język C++ w programie Visual Studio](../overview/visual-cpp-in-visual-studio.md)<br/>
[Co nowego w kompilatorze języka C++ w programie Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
[Ulepszenia zgodności języka C++ w programie Visual Studio](../overview/cpp-conformance-improvements.md)<br/>
