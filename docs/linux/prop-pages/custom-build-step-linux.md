---
title: Właściwości niestandardowego kroku kompilacji (Linux C++)
ms.date: 10/17/2017
ms.assetid: 77a9c1fb-7c41-4a9b-9418-18ac17ce4e74
ms.openlocfilehash: 5e6580263e63547e3564eaee260158a312e5fa6a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644707"
---
# <a name="custom-build-step-properties-linux-c"></a>Właściwości niestandardowego kroku kompilacji (Linux C++)

Właściwość | Opis
--- | ---
Wiersz polecenia | Polecenie wykonywane przez krok niestandardowej kompilacji.
Opis | Komunikat, który jest wyświetlany podczas wykonywania kroku niestandardowej kompilacji.
Dane wyjściowe | Plik wyjściowy, generowany przez krok niestandardowej kompilacji. To ustawienie jest wymagane, aby kompilacje przyrostowe działały poprawnie.
{1&gt;Dodatkowe zależności&lt;1} | Rozdzielana średnikami lista wszelkich dodatkowych plików wejściowych dla kroku niestandardowej kompilacji.
Wykonaj po i wykonaj przed | Te opcje definiują, kiedy krok niestandardowej kompilacji jest uruchamiany w procesie kompilacji w stosunku do wymienionych celów. Najczęściej wymienione cele to BuildGenerateSources, BuildCompile i BuildLink, ponieważ stanowią one najważniejsze kroki procesu kompilacji. Inne często wymienione cele to Midl, CLCompile i Link.
Traktuj dane wyjściowe jako zawartość | Ta opcja jest przydatna tylko dla aplikacji Microsoft Store lub Windows Phone, które obejmują wszystkie pliki zawartości w pakiecie .appx.