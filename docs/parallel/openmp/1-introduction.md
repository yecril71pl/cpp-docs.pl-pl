---
title: 1. Wprowadzenie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c42e72bc-0e31-4b1c-b670-cd82673c0c5a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ce963d312d145e26567a5902f32e45735eb1d89
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438421"
---
# <a name="1-introduction"></a>1. Wprowadzenie

W tym dokumencie określa zbiór dyrektywy kompilatora, funkcje i zmienne środowiskowe, które mogą służyć do określania równoległości pamięci współużytkowanej w ramach programów C i C++. Funkcje opisane w niniejszym dokumencie jest nazywane zbiorczo *interfejsu programu aplikacji (API) OpenMP C/C++*. Celem tej specyfikacji jest zapewnienie modelu programowania równoległego umożliwia program będzie działał w ramach architektury pamięci współużytkowanej pochodzących od różnych dostawców. OpenMP C/C++ API będą obsługiwane przez kompilatory od wielu dostawców. Więcej informacji na temat OpenMP, w tym *interfejs aplikacji OpenMP Fortran*, można znaleźć w następującej witrynie sieci web:

[http://www.openmp.org](http://www.openmp.org)

Dyrektywy, funkcje i zmienne środowiskowe zdefiniowane w tym dokumencie pozwoli użytkownikom tworzenie i zarządzanie nimi programów do równoległego przetwarzania, umożliwiając przenoszenia. Dyrektywy rozszerzenia C sekwencyjne programowania C++ modelu za pomocą jednego programu wielu konstrukcji danych (zawiera system SPMD), konstrukcje podziału pracy i konstrukcje synchronizacji i zapewniają obsługę udostępniania i prywatyzacji danych. Kompilatory, które obsługują OpenMP C i C++ interfejsu API będzie zawierać opcji wiersza polecenia kompilatora, który aktywuje i umożliwia interpretacji wszystkich OpenMP, dyrektywy kompilatora.