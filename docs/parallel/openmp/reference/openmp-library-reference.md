---
title: Odwołanie do biblioteki OpenMP
ms.date: 12/02/2019
ms.assetid: a25188c6-edde-43d0-84b5-780e797b08fc
ms.openlocfilehash: b61eb356b782b3cd17557827734a706e0761a2a8
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810741"
---
# <a name="openmp-library-reference"></a>Odwołanie do biblioteki OpenMP

Oferuje linki do konstrukcji używanych w interfejsie API OpenMP.

Wizualna C++ implementacja standardu OpenMP obejmuje następujące konstrukcje.

|Konstrukcja|Opis|
|---------------|-----------------|
|[Dyrektywy](openmp-directives.md)|Zawiera łącza do dyrektyw używanych w interfejsie API OpenMP.|
|[Klauzule](openmp-clauses.md)|Zawiera łącza do klauzul używanych w interfejsie API OpenMP.|
|[Funkcje](openmp-functions.md)|Zawiera łącza do funkcji używanych w interfejsie API OpenMP.|
|[Zmienne środowiskowe](openmp-environment-variables.md)|Oferuje linki do zmiennych środowiskowych używanych w interfejsie API OpenMP.|

Funkcje biblioteki C++ wykonawczej Visual OpenMP są zawarte w następujących bibliotekach.

|Biblioteka wykonawcza OpenMP|Cechy|
|------------------------------|---------------------|
|VCOMP.LIB|Wielowątkowy, dynamiczny link (Biblioteka importowana dla VCOMP140. DLL).|
|VCOMPD.LIB|Wielowątkowy, dynamiczny link (Biblioteka importowana dla VCOMP140D. DLL) (Debuguj)|

Jeśli _DEBUG jest zdefiniowany w kompilacji i jeśli `#include <omp.h>` jest w kodzie źródłowym, VCOMPD. LIB będzie domyślną lib, w przeciwnym razie VCOMP. Zostanie użyta Biblioteka LIB.

Możesz użyć [/NODEFAULTLIB (Ignoruj biblioteki)](../../../build/reference/nodefaultlib-ignore-libraries.md) , aby usunąć domyślną lib i jawnie połączyć z dowolnie wybraną lib.

Biblioteki DLL OpenMP znajdują się w C++ katalogu redystrybucyjnym wizualizacji i muszą być dystrybuowane z aplikacjami, które używają OpenMP.

## <a name="see-also"></a>Zobacz także

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)
