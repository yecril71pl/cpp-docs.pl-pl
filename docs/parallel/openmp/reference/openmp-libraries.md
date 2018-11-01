---
title: Biblioteki OpenMP
ms.date: 10/24/2018
ms.assetid: f89abf97-67e3-4327-bc30-43f85b9533a2
ms.openlocfilehash: 75f772c953a2120a02f72d8bdfc73c1baaaef390
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530341"
---
# <a name="openmp-libraries"></a>Biblioteki OpenMP

W tym artykule omówiono pliki .lib, które tworzą biblioteki wykonawczej OpenMP w programie Visual C++.

Następujące biblioteki zawierają funkcje biblioteki czasu wykonywania Visual C++ OpenMP.

|Biblioteka środowiska uruchomieniowego OpenMP|Właściwości|
|------------------------------|---------------------|
|VCOMP.LIB|Link wielowątkowych i dynamiczny (bibliotekę importowaną VCOMP. LIB).|
|VCOMPD.LIB|Link wielowątkowych i dynamiczny (bibliotekę importowaną VCOMPD. POKRYWY) (debugowanie)|

Jeśli _DEBUG jest zdefiniowany w kompilacji i `#include omp.h` znajduje się w kodzie źródłowym, VCOMPD. LIB będzie ignorowana przez tę domyślną. W przeciwnym razie VCOMP. Lib — będzie używana.

Możesz użyć [/nodefaultlib (Ignoruj biblioteki)](../../../build/reference/nodefaultlib-ignore-libraries.md) usunąć biblioteki domyślne i jawnie utworzyć łącze z lib wybranych przez użytkownika.

Biblioteki DLL OpenMP znajdują się w katalogu pakiet redystrybucyjny Visual C++ i muszą być dystrybuowane za pomocą aplikacji, które używają OpenMP.

## <a name="see-also"></a>Zobacz także

[Odwołanie do biblioteki](openmp-library-reference.md)
