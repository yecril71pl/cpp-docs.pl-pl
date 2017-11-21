---
title: "Właściwości zdalnego archiwum (C++ Linux) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 9/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ee1e44c-8337-4c3a-b2f3-35e4be954f9f
author: mikeblome
ms.author: mblome
manager: ghogen
f1_keywords:
- VC.Project.Ar.CreateIndex
- VC.Project.Ar.CreateThinArchive
- VC.Project.Ar.NoWarnOnCreate
- VC.Project.Ar.TruncateTimestamp
- VC.Project.Ar.SuppressStartupBanner
- VC.Project.Ar.Verbose
- vc.project.AdditionalOptionsPage
- VC.Project.Ar.OutputFile
- VC.Project.VCConfiguration.BuildLogFile
ms.openlocfilehash: 402fa1f752b311014c828027e45a92a3dc6a2917
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
