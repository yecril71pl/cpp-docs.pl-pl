---
title: Błąd PRJ0032 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0032
helpviewer_keywords:
- PRJ0032
ms.assetid: bc6acbea-4041-4237-8b5a-f0434705d89f
ms.openlocfilehash: f1f292f3979c993a8fa8cb8ff44653ac7124b121
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499843"
---
# <a name="project-build-error-prj0032"></a>Błąd PRJ0032 kompilacji projektu

Właściwość 'Wyniki' dla projektów na poziomie niestandardowego kroku kompilacji zawiera makra, które ewaluowane jest jako "macro_expansion".

Niestandardowego kroku kompilacji w projekcie ma nieprawidłowe dane wyjściowe, prawdopodobnie z powodu problemu z oceny makra. Ten błąd może również oznaczać, że ścieżka jest nieprawidłowo sformułowany, zawierające znaki lub kombinacje znaków, które nie są dozwolone w ścieżce pliku.

Aby rozwiązać ten problem, napraw makra, lub usuń specyfikację ścieżki. Oceniono ścieżka jest ścieżką bezwzględną z katalogu projektu.