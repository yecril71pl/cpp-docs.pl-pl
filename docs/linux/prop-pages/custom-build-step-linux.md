---
title: "Właściwości kroku kompilacji niestandardowej (Linux C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77a9c1fb-7c41-4a9b-9418-18ac17ce4e74
author: mikeblome
ms.author: mblome
manager: ghogen
f1_keywords:
- VC.Project.IVCEventTool.CommandLine
- VC.Project.IVCEventTool.Description
- VC.Project.IVCEventTool.ExcludedFromBuild
- VC.Project.VCConfiguration.BuildLogFile
ms.openlocfilehash: 77d483e9d4dc74cbe9ba2736a26561bb410fa6ca
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="custom-build-step-properties-linux-c"></a>Właściwości kroku kompilacji niestandardowej (Linux C++)


Właściwość | Opis
--- | ---
Wiersz polecenia | Polecenie wykonywane przez krok niestandardowej kompilacji.
Opis | Komunikat, który jest wyświetlany podczas wykonywania kroku niestandardowej kompilacji.
Dane wyjściowe | Plik wyjściowy, generowany przez krok niestandardowej kompilacji. To ustawienie jest wymagane, aby kompilacje przyrostowe działały poprawnie.
Dodatkowe zależności | Rozdzielana średnikami lista wszelkich dodatkowych plików wejściowych dla kroku niestandardowej kompilacji.
Wykonanie i wykonać przed | Te opcje definiują, kiedy krok niestandardowej kompilacji jest uruchamiany w procesie kompilacji w stosunku do wymienionych celów. Najczęściej wymienione cele to BuildGenerateSources, BuildCompile i BuildLink, ponieważ stanowią one najważniejsze kroki procesu kompilacji. Inne często wymienione cele to Midl, CLCompile i Link.
Traktuj dane wyjściowe jako zawartość | Ta opcja jest przydatna tylko dla aplikacji Windows Store lub Windows Phone, które obejmują wszystkie pliki zawartości w pakiecie .appx.