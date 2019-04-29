---
title: Odwołanie do biblioteki OpenMP
ms.date: 03/20/2019
ms.assetid: a25188c6-edde-43d0-84b5-780e797b08fc
ms.openlocfilehash: 6f4bbeca54bff1fc44a3576362edca9c30926d5a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362520"
---
# <a name="openmp-library-reference"></a>Odwołanie do biblioteki OpenMP

Zawiera łącza do konstrukcji używanych w interfejsie API OpenMP.

Implementacja języka Visual C++ OpenMP standard obejmuje następujące elementy.

|Konstrukcja|Opis|
|---------------|-----------------|
|[Dyrektywy](openmp-directives.md)|Zawiera łącza do informacji o dyrektywach używany w interfejsie API OpenMP.|
|[Klauzule](openmp-directives.md)|Zawiera łącza do klauzul używany w interfejsie API OpenMP.|
|[Funkcje](openmp-functions.md)|Zawiera łącza do funkcji używanych w interfejsie API OpenMP.|
|[Zmienne środowiskowe](openmp-environment-variables.md)|Zawiera łącza do zmiennych środowiskowych, używany w interfejsie API OpenMP.|

Element wizualny C++ OpenMP, funkcje biblioteki wykonawczej są zawarte w następujących bibliotek.

|Biblioteka środowiska uruchomieniowego OpenMP|Właściwości|
|------------------------------|---------------------|
|VCOMP.LIB|Link wielowątkowych i dynamiczny (bibliotekę importowaną VCOMP. LIB).|
|VCOMPD.LIB|Link wielowątkowych i dynamiczny (bibliotekę importowaną VCOMPD. POKRYWY) (debugowanie)|

Jeśli _DEBUG jest zdefiniowany w kompilacji i `#include omp.h` znajduje się w kodzie źródłowym, VCOMPD. LIB będzie lib domyślny, w przeciwnym razie VCOMP. Lib — będzie używana.

Możesz użyć [/nodefaultlib (Ignoruj biblioteki)](../../../build/reference/nodefaultlib-ignore-libraries.md) usunąć biblioteki domyślne i jawnie utworzyć łącze z lib wybranych przez użytkownika.

Biblioteki DLL OpenMP znajdują się w katalogu pakiet redystrybucyjny Visual C++ i muszą być dystrybuowane za pomocą aplikacji, które używają OpenMP.

## <a name="see-also"></a>Zobacz także

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)