---
title: Biblioteki OpenMP | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/24/2018
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
ms.openlocfilehash: 7620b0ea710a5474fbbbf614691ceeb1e5cc945e
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062005"
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
