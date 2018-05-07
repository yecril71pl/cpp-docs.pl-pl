---
title: Właściwości kroku kompilacji niestandardowej (Linux C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/17/2017
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 77a9c1fb-7c41-4a9b-9418-18ac17ce4e74
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 0ec787826a09379732ac00fa858d32f05cf8025b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="custom-build-step-properties-linux-c"></a>Właściwości kroku kompilacji niestandardowej (Linux C++)

Właściwość | Opis
--- | ---
Wiersz polecenia | Polecenie wykonywane przez krok niestandardowej kompilacji.
Opis | Komunikat, który jest wyświetlany podczas wykonywania kroku niestandardowej kompilacji.
Dane wyjściowe | Plik wyjściowy, generowany przez krok niestandardowej kompilacji. To ustawienie jest wymagane, aby kompilacje przyrostowe działały poprawnie.
{1&gt;Dodatkowe zależności&lt;1} | Rozdzielana średnikami lista wszelkich dodatkowych plików wejściowych dla kroku niestandardowej kompilacji.
Wykonanie i wykonać przed | Te opcje definiują, kiedy krok niestandardowej kompilacji jest uruchamiany w procesie kompilacji w stosunku do wymienionych celów. Najczęściej wymienione cele to BuildGenerateSources, BuildCompile i BuildLink, ponieważ stanowią one najważniejsze kroki procesu kompilacji. Inne często wymienione cele to Midl, CLCompile i Link.
Traktuj dane wyjściowe jako zawartość | Ta opcja jest znaczący tylko w przypadku aplikacji Microsoft Store lub Windows Phone, które zawiera wszystkie pliki zawartości w pakiecie .appx.