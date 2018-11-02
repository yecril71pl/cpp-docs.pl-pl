---
title: 1. Wprowadzenie
ms.date: 11/04/2016
ms.assetid: c42e72bc-0e31-4b1c-b670-cd82673c0c5a
ms.openlocfilehash: b365ff828fd7dc2b7d9d3136a4fbfb68c43902ce
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554716"
---
# <a name="1-introduction"></a>1. Wprowadzenie

W tym dokumencie określa zbiór dyrektywy kompilatora, funkcje i zmienne środowiskowe, które mogą służyć do określania równoległości pamięci współużytkowanej w ramach programów C i C++. Funkcje opisane w niniejszym dokumencie jest nazywane zbiorczo *interfejsu programu aplikacji (API) OpenMP C/C++*. Celem tej specyfikacji jest zapewnienie modelu programowania równoległego umożliwia program będzie działał w ramach architektury pamięci współużytkowanej pochodzących od różnych dostawców. OpenMP C/C++ API będą obsługiwane przez kompilatory od wielu dostawców. Więcej informacji na temat OpenMP, w tym *interfejs aplikacji OpenMP Fortran*, można znaleźć w następującej witrynie sieci web:

[http://www.openmp.org](http://www.openmp.org)

Dyrektywy, funkcje i zmienne środowiskowe zdefiniowane w tym dokumencie pozwoli użytkownikom tworzenie i zarządzanie nimi programów do równoległego przetwarzania, umożliwiając przenoszenia. Dyrektywy rozszerzenia C sekwencyjne programowania C++ modelu za pomocą jednego programu wielu konstrukcji danych (zawiera system SPMD), konstrukcje podziału pracy i konstrukcje synchronizacji i zapewniają obsługę udostępniania i prywatyzacji danych. Kompilatory, które obsługują OpenMP C i C++ interfejsu API będzie zawierać opcji wiersza polecenia kompilatora, który aktywuje i umożliwia interpretacji wszystkich OpenMP, dyrektywy kompilatora.