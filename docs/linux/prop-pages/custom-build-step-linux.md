---
title: Niestandardowe właściwości kroku kompilacji (Linux C++)
ms.date: 06/07/2019
ms.assetid: 77a9c1fb-7c41-4a9b-9418-18ac17ce4e74
ms.openlocfilehash: 67b281e245c4fff8f37baff8875cbc3dc84ca718
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441330"
---
# <a name="custom-build-step-properties-linux-c"></a>Niestandardowe właściwości kroku kompilacji (Linux C++)

::: moniker range="vs-2015"

Obsługa systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych.

::: moniker-end

::: moniker range=">=vs-2017"

| Właściwość | Opis |
|--|--|
| Wiersz polecenia | Polecenie wykonywane przez krok niestandardowej kompilacji. |
| Opis | Komunikat, który jest wyświetlany podczas wykonywania kroku niestandardowej kompilacji. |
| Dane wyjściowe | Plik wyjściowy, generowany przez krok niestandardowej kompilacji. To ustawienie jest wymagane, aby kompilacje przyrostowe działały poprawnie. |
| {1&gt;Dodatkowe zależności&lt;1} | Rozdzielana średnikami lista wszelkich dodatkowych plików wejściowych dla kroku niestandardowej kompilacji. |
| Wykonaj po i wykonaj przed | Te opcje definiują, kiedy krok niestandardowej kompilacji jest uruchamiany w procesie kompilacji w stosunku do wymienionych celów. Najczęściej wymienione cele to BuildGenerateSources, BuildCompile i BuildLink, ponieważ stanowią one najważniejsze kroki procesu kompilacji. Inne często wymienione cele to Midl, CLCompile i Link. |
| Traktuj dane wyjściowe jako zawartość | Ta opcja ma znaczenie tylko w przypadku aplikacji Microsoft Store lub Windows Phone, które obejmują wszystkie pliki zawartości w pakiecie. appx. |

::: moniker-end
