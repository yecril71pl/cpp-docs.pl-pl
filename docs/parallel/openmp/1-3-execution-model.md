---
title: 1.3 Model wykonania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 85ae8bc4-5bf0-45e0-a45f-02de9adaf716
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c284563a47d21abc9a1dacf045238449d64205d5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394013"
---
# <a name="13-execution-model"></a>1.3 Model wykonania

OpenMP używa modelu przyłączaniem do rozwidlenia wykonywanie równoległe. Mimo że ten model rozwidlenia sprzężenia mogą być przydatne w przypadku rozwiązywania różnych problemów, jest on nieco zoptymalizowanych pod kątem dużych aplikacji opartych na tablicy. OpenMP jest przeznaczona do programów obsługi, które będą wykonywane poprawnie zarówno jako równoległych programów (wielu wątków wykonania i cała biblioteka obsługi OpenMP) oraz programy sekwencyjnego (dyrektywy ignorowane i proste biblioteki klas zastępczych OpenMP). Jednak jest możliwe i możliwość tworzenia program, który nie działają prawidłowo, gdy są wykonywane sekwencyjnie. Ponadto różny stopień równoległości może spowodować różnych wyników liczbowych ze względu na zmiany w skojarzeniu operacji numerycznych. Na przykład zmniejszenie o dodanie serial mogą mieć różnych wzorców skojarzenia dodanie niż równoległych redukcji. Te różne skojarzenia mogą ulec zmianie wyniki dodawania zmiennoprzecinkowych.

Program napisany za pomocą interfejsu API języka C/C++ OpenMP rozpoczyna wykonywanie jako pojedynczy wątek wykonywania o nazwie *głównym wątku*. Główny wątek wykonuje w regionie serial, dopóki nie zostanie osiągnięty pierwszy konstrukcja równoległa. W interfejsie API języka C/C++ OpenMP **równoległe** dyrektywa stanowi konstrukcja równoległa. Po napotkaniu konstrukcja równoległa głównego wątku utworzy zespół wątków, i wzorcem staje się głównej zespołu. Każdy wątek w zespół wykonuje instrukcje dynamiczne zakresu równoległego regionu, z wyjątkiem konstrukcje podziału pracy. Konstrukcje podziału pracy musi być napotykanych przez wszystkie wątki zespołu w tej samej kolejności i co najmniej jeden z wątków wykonywane są instrukcje w ramach skojarzone ze strukturalnego bloku. Możesz też dorozumianych na końcu konstrukcji podziału pracy, bez `nowait` klauzula jest wykonywana przez wszystkie wątki w zespole.

Jeśli wątek modyfikuje obiektów udostępnionych, dotyczy nie tylko własnego środowiska wykonawczego, a także porównanie tych innych wątków w programie. Modyfikacja jest gwarantowane jest pełny, z punktu widzenia jednego z innych wątków w następnym punkcie sekwencji (zgodnie z definicją w języku podstawowej), tylko wtedy, gdy obiekt został zadeklarowany jako volatile. W przeciwnym razie zmiany może być kompletny po pierwszych modyfikowanie wątku i następnie (lub jednocześnie) występują inne wątki **opróżniania** dyrektywę, który określa obiekt (jawnie lub niejawenie). Należy pamiętać, że w przypadku **opróżniania** dyrektyw, które są też dorozumianych przez inne dyrektywy OpenMP nie są wystarczające, aby upewnić się, w żądanej kolejności efekty uboczne, odpowiada za programisty podać dodatkowe, jawna  **Flush** dyrektywy.

Po zakończeniu konstrukcja równoległa w niejawne barierę synchronizować wątków w zespole, a tylko główny wątek kontynuuje wykonywanie. W jednym programie można określić dowolną liczbę równoległych konstrukcji. Co w efekcie program może rozwidlenie i połączyć wiele razy w czasie wykonywania.

OpenMP C/C++ API umożliwia programistom użyć dyrektyw w funkcje wywołane z wnętrza równoległe konstrukcje. Dyrektyw, które nie są wyświetlane w zakresie leksykalnym konstrukcja równoległa, ale może znajdować się w zakresie dynamicznych są nazywane *oddzielone* dyrektywy. Dyrektywy oddzielone zapewniają programistów możliwość wykonywania głównych części programu równolegle z tylko minimalne zmiany do programu sekwencyjne. Dzięki tej funkcji Użytkownicy mogą kodu równoległe konstrukcje w górnym poziomy drzewa wywołań programu i użyj dyrektywy, aby kontrolować wykonywanie we wszystkich wywoływanych funkcji.

Funkcje, które zapisu do tego samego pliku może spowodować w danych wyjściowych, w którym dane zapisane przez inne wątki pojawia się w kolejności niedeterministyczne danych wyjściowych niezsynchronizowane wywołania do C i C++. Podobnie niezsynchronizowane wywołania do funkcji, które odczytują z tego samego pliku wejściowego może odczytać dane w kolejności jednoznaczne wyniki. Niezsynchronizowane użycia operacji We/Wy, tak, aby każdy wątek uzyskuje dostęp do innego pliku, jest taki sam jak wykonanie szeregowe funkcji we/wy.