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
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: ae749fa161dba2957f3e621ce42c610153594e66
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
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