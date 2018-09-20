---
title: Biblioteki OpenMP | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: f89abf97-67e3-4327-bc30-43f85b9533a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c9a4ccfefeaeb9446731027db44b849233bfefd6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391218"
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

## <a name="see-also"></a>Zobacz też

[Odwołanie do biblioteki](../../../parallel/openmp/reference/openmp-library-reference.md)