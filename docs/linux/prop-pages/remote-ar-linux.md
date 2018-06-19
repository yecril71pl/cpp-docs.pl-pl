---
title: Właściwości zdalnego archiwum (C++ Linux) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 9/26/2017
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 5ee1e44c-8337-4c3a-b2f3-35e4be954f9f
author: mikeblome
ms.author: mblome
f1_keywords: []
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 004e015b7e5ad8a99b3bea2bf21b7b598f2fedbd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33328656"
---
# <a name="remote-archive-properties-c-linux"></a>Właściwości zdalnego archiwum (C++ Linux)

Właściwość | Opis
--- | ---
Utwórz indeks archiwum | Utwórz indeks archiwum (cf. ranlib).  Może to przyspieszyć konsolidowanie i ograniczyć zależność w obrębie własnej biblioteki.
Tworzenie elastycznej archiwum | Tworzenie elastycznej archiwum.  Archiwum alokowania zawiera ścieżki względne do obiektów zamiast osadzania obiektów.  Przełączanie między uproszczonym i normalnym wymaga usunięcia istniejącej biblioteki.
Bez ostrzeżenia o utworzeniu | Nie Ostrzegaj, jeśli po utworzeniu biblioteki.
TRUNCATE sygnatury czasowej | Użyj wartości zero dla sygnatur czasowych oraz identyfikatorów UID i GID.
Pomiń Baner startowy | Nie pokazuj numeru wersji.
Pełny | Pełny
Dodatkowe opcje | Dodatkowe opcje.
Plik wyjściowy | Opcja/out przesłania domyślną nazwę i lokalizację programu tworzonego przez bibliotekę.
Archiver | Określa program do wywołania podczas łączenia statycznych obiektów lub ścieżka do archiver w systemie zdalnym.
Limit czasu archiver | Limit zdalnego archiver czasu w milisekundach.
Kopiuj dane wyjściowe | Określa, czy można skopiować pliku danych wyjściowych kompilacji z systemu zdalnego na komputerze lokalnym.
