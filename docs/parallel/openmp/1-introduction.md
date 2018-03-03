---
title: 1. Wprowadzenie | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: c42e72bc-0e31-4b1c-b670-cd82673c0c5a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f850e236ebfd056da93700df06ec830e5a573284
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="1-introduction"></a>1. Wprowadzenie
Ten dokument określa zbiór dyrektywy kompilatora, funkcje i zmienne środowiskowe, które mogą służyć do określenia pamięci współużytkowanej równoległości w programach C i C++. Funkcje opisane w tym dokumencie jest nazywane zbiorczo *interfejsu programu aplikacji (API) OpenMP C/C++*. Celem tej specyfikacji jest zapewnienie modelu programowania równoległego umożliwia programowi jako przenośny między architekturami pamięci współużytkowanej pochodzących od różnych dostawców. Interfejs API C/C++ OpenMP będą obsługiwane przez kompilatory od wielu dostawców. Więcej informacji na temat OpenMP, łącznie z *interfejs aplikacji Fortran OpenMP*, można znaleźć w następującej witrynie sieci web:  
  
 [http://www.OpenMP.org](http://www.openmp.org)  
  
 Dyrektywy, funkcje i zmienne środowiskowe zdefiniowane w tym dokumencie pozwoli użytkownikom na tworzenie i zarządzanie nimi równoległych programy, umożliwiając przenośność. Dyrektywy rozszerzyć C sekwencyjnych programowania w języku C++ modelu z jednego programu wiele konstrukcji danych (zawiera system SPMD), konstrukcje podziału pracy oraz elementów składowych synchronizacji i zapewniają obsługę do udostępniania i prywatyzacji danych. Kompilatory, które obsługują Openmpc i C++ interfejsu API będzie zawierać opcji wiersza polecenia do kompilatora aktywuje i umożliwiający interpretacji wszystkich OpenMP — dyrektywy kompilatora.