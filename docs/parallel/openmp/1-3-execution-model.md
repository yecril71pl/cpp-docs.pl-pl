---
title: 1.3 Model wykonania | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 85ae8bc4-5bf0-45e0-a45f-02de9adaf716
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: dddc4c10a77ca5dd277435837169478e0d5daca5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="13-execution-model"></a>1.3 Model wykonania
OpenMP wykorzystuje model sprzężenia rozwidlenia wykonywanie równoległe. Chociaż ten model rozwidlenia sprzężenia mogą być przydatne podczas rozwiązywania szerokiej gamy problemów, nieco jest dostosowane dla dużych aplikacji opartych na tablicy. OpenMP jest przeznaczony do programów obsługi, które będą wykonywane prawidłowo zarówno jako programy równoległe (wiele wątków wykonywania i pełne Biblioteka obsługi OpenMP) i jako programy sekwencyjnych (dyrektywy ignorowane i proste biblioteki klas zastępczych OpenMP). Jednak jest możliwe i zezwolić na opracowanie program, który nie zadziała poprawnie, gdy wykonywane sekwencyjnie. Ponadto różne stopień równoległości może spowodować różnych wyników liczbowych ze względu na zmiany w skojarzeniu operacji liczbowych. Na przykład zmniejszenie dodanie serial mogą mieć różnych wzorzec skojarzenia dodanie niż zmniejszenie równoległych. Różne skojarzenia może zmienić wyniki dodawanie liczb zmiennoprzecinkowych.  
  
 Program napisany przy użyciu interfejsu API C/C++ OpenMP rozpoczyna wykonanie jako pojedynczego wątku wykonywania o nazwie *głównego wątku*. Głównego wątku jest wykonywana w regionie szeregowy do czasu napotkano pierwszy konstrukcja równoległych. W interfejsie API C/C++ OpenMP **równoległych** dyrektywa stanowi konstrukcję równoległych. W przypadku równoległego konstrukcja wątku głównego tworzy zespołu wątków i wzorzec staje się głównym zespołu. Każdy wątek w zespole wykonuje instrukcje dynamicznego zakresu równoległego regionu, z wyjątkiem konstrukcje podziału pracy. Konstrukcje podziału pracy musi wystąpić przez wszystkie wątki zespołu w tej samej kolejności, a instrukcje skojarzone strukturalnego bloku są wykonywane przez jedną lub więcej wątków. Bariera niejawnego na końcu konstrukcji podziału pracy bez `nowait` klauzuli jest wykonywane przez wszystkie wątki w zespole.  
  
 Jeśli wątek modyfikuje obiekt współużytkowany, dotyczy nie tylko własnego środowiska wykonawczego, ale także te inne wątki w programie. Gwarantuje to pełny, z punktu widzenia jednego z innych wątków na następny punkt sekwencji (zgodnie z definicją w podstawowym języku) tylko wtedy, gdy obiekt jest zadeklarowany jako nietrwałe modyfikacji. W przeciwnym razie modyfikacja gwarantuje to pełną po najpierw modyfikowanie wątku, a następnie (lub jednocześnie) wystąpić inne wątki **opróżnić** dyrektywa określająca obiekt (niejawnie lub jawnie). Należy pamiętać, że w przypadku **opróżnić** dyrektywy, które są implikowana przez inne dyrektywy OpenMP nie są wystarczające, aby zapewnić odpowiednią kolejność efekty uboczne, odpowiada programisty podać dodatkowe, jawne  **Flush** dyrektywy.  
  
 Po zakończeniu konstrukcji równoległe wątki zespołu synchronizować niejawne bariery, a tylko wątku głównego kontynuuje wykonywanie. W jednym programie można określić dowolną liczbę równoległych konstrukcje. W związku z tym programem może rozwidlania i Dołącz wiele razy podczas wykonywania.  
  
 Interfejs API C/C++ OpenMP umożliwia deweloperom użyj dyrektywy w funkcjach wywoływanych z wewnątrz równoległe konstrukcje. Dyrektywy, które nie są wyświetlane w zakresie leksykalne konstrukcję równoległe, ale może znajdować się w zakresie dynamiczne są nazywane *oddzielone* dyrektywy. Dyrektywy oddzielone dają programistów możliwość wykonywania głównych części programu równolegle z tylko minimalne zmiany do programu sekwencyjnych. Dzięki tej funkcji Użytkownicy mogą kodu równoległe konstrukcje w najwyższego poziomy drzewa wywołania programu i użyj dyrektywy, aby kontrolować wykonywanie w żadnej funkcji o nazwie.  
  
 Funkcje, które zapisu do tego samego pliku może spowodować wyjściowego, w którym dane zapisane przez inne wątki pojawia się w kolejności niedeterministyczne wyjściowe niezsynchronizowane wywołania do C i C++. Podobnie niezsynchronizowane wywołania funkcji, które zapoznały się z tego samego pliku wejściowym może odczytywać dane w kolejności niedeterministyczne. Niezsynchronizowane użyj operacji We/Wy, tak, aby każdy wątek uzyskuje dostęp do innego pliku, jest taki sam jak serial wykonywanie funkcje We/Wy.